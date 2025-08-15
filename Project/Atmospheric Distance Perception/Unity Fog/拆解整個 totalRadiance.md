好的，沒有問題。身為工程師，我們來對 `totalRadiance += transmittance * scattering * (phase * blendValue.rgb + probeRadiance);` 這行程式碼進行一次最徹底的「逆向工程」，追溯每一個變數的完整生命週期，並將它們與 Unity Editor 中的參數一一對應。

這行程式碼是體積渲染方程積分式的核心實現，發生在 `VolumetricLighting.compute` 的主迴圈中，其目的是計算單一「體素薄片」所貢獻的光量，並將其累加。

---

### 拆解 `totalRadiance += transmittance * scattering * (phase * blendValue.rgb + probeRadiance);`

#### 1. `totalRadiance`

- **定義**: 一個 `float3` 變數，作為累加器使用 1。它的初始值為 0 2。在迴圈的每一步，它都會累加上當前體素薄片貢獻的亮度，最終成為該視線路徑上的總「Fog Luminance」。
    
- **追溯**: 它的值完全由 `+=` 運算子右側的所有變數決定。
    
- **Unity Editor 關聯**: 無直接關聯。它是一個運行時的計算結果。
    

#### 2. `transmittance`

- **定義**: 一個 `float` 純量，代表從當前體素薄片到攝影機的透射率（光線能量剩餘比例） 3。
    
- **追溯**:
    
    1. `transmittance` 由 `TransmittanceFromOpticalDepth(opticalDepth)` 計算得出 444。
        
    2. `opticalDepth` 是另一個累加器，它在迴圈的每一步都會加上 `0.5 * blendValue.a` 兩次 5555。
        
    3. `blendValue.a` 儲存了當前薄片的光學深度，其值為 `extinction * dt` 6。
        
    4. `extinction` 來自 `_VBufferDensity` 紋理的 alpha 通道 7，這個值是在
        
        `VolumeVoxelization.compute` 中計算的。
        
    5. 在
        
        `VolumeVoxelization.compute` 中，`voxelExtinction = _HeightFogBaseExtinction * heightMultiplier` 8。
        
    6. `_HeightFogBaseExtinction` 來自 C# 腳本 `Fog.cs`，由 `meanFreePath` 取倒數得到 9。
        
- **Unity Editor 關聯**:
    
    - **Fog Override** > **Fog Attenuation Distance**。
        

#### 3. `scattering`

- **定義**: 一個 `float3` 向量，代表當前體素薄片的散射係數，決定了霧散射光的顏色和強度。
    
- **追溯**:
    
    1. `scattering` 直接從 `_VBufferDensity` 紋理的 `rgb` 通道讀取 10。
        
    2. 這個值是在
        
        `VolumeVoxelization.compute` 中被寫入的，其計算公式為 `voxelScattering = _HeightFogBaseScattering.xyz * heightMultiplier` 11。
        
    3. `_HeightFogBaseScattering` 來自 C# 腳本 `Fog.cs`。
        
    4. 在
        
        `Fog.cs` 中，`_HeightFogBaseScattering` 的值由 `extinction` 和 `albedo` 相乘得到。`extinction` 來自 `meanFreePath`，`albedo` 則直接來自 `albedo.value` 12。
        
- **Unity Editor 關聯**:
    
    - **Fog Override** > **Fog Attenuation Distance**。
        
    - **Fog Override** > **Albedo**。
        

#### 4. `phase`

- **定義**: 一個 `float` 純量，由相位函數 (Phase Function) 計算得出，用於描述光線被霧粒子散射後的方向性分佈。
    
- **追溯**:
    
    1. 在 `VolumetricLighting.compute` 中，`phase` 的計算分為兩種情況：
        
        - 對於直接光和本地光，
            
            `phase = CornetteShanksPhasePartVarying(anisotropy, cosTheta)` 131313131313131313。
            
        - 對於環境光，
            
            `phase = _CornetteShanksConstant` 14。
            
    2. `CornetteShanksPhasePartVarying` 函式在 `VolumeRendering.hlsl` 中定義 15。其主要輸入是
        
        `anisotropy`。
        
    3. `anisotropy` 這個變數來自 `_GlobalFogAnisotropy` 16，它是在 C# 層設定的全域變數。
        
    4. 在
        
        `Fog.cs` 中，`_GlobalFogAnisotropy` 的值被設定為 `anisotropy.value` 17。
        
- **Unity Editor 關聯**:
    
    - **Fog Override** > (Advanced) **Anisotropy**。
        

#### 5. `blendValue.rgb`

- **定義**: 一個 `float3` 向量，代表了所有**直接光源**（方向光、點光、聚光燈等）照射到當前體素薄片後，經過時間性降噪（Temporal Reprojection）處理後的內散射光。
    
- **追溯**:
    
    1. `blendValue.rgb` 來自於對 `aggregateLighting` 變數的處理結果 18。
        
    2. `aggregateLighting` 變數是 `EvaluateVoxelLightingDirectional`、`EvaluateVoxelLightingLocal` 和 `EvaluateVoxelDiffuseGI` 函式的結果總和 19。
        
    3. `EvaluateVoxelLightingDirectional` 函式會遍歷 `_DirectionalLightDatas` 緩衝區，計算每個方向光的光照和陰影 20。
        
    4. `EvaluateVoxelLightingLocal` 函式會遍歷 `_LightDatas` 緩衝區，計算每個本地光源的光照和陰影 21。
        
- **Unity Editor 關聯**:
    
    - 場景中所有**啟用**的 **Directional Light** 元件。
        
    - 場景中所有**啟用**的 **Point Light**, **Spot Light**, **Area Light** 元件。
        
    - 這些光源的 **Intensity**, **Color**, **Range** 以及 **Shadow** 設定等都會影響最終結果。
        

#### 6. `probeRadiance`

- **定義**: 一個 `float3` 向量，代表了來自**間接光源**（天空、環境探針、GI）照射到當前體素薄片後的內散射光。
    
- **追溯**:
    
    1. `probeRadiance` 由 `probeInScatteredRadiance * TransmittanceIntegralHomogeneousMedium(extinction, dt)` 計算得出 22。
        
    2. `probeInScatteredRadiance` 在迴圈外被預先計算，來自 `EvaluateVolumetricAmbientProbe(ray.centerDirWS)` 23。
        
    3. `EvaluateVolumetricAmbientProbe` 在 `VolumetricLighting.compute` 中定義，它會從 `_VolumetricAmbientProbeBuffer` 中採樣球諧光照係數 24。
        
    4. `_VolumetricAmbientProbeBuffer` 的數據由 CPU 端的 `SkyManager` 根據當前的天空設定和烘焙的 GI 數據填充。
        
- **Unity Editor 關聯**:
    
    - **Sky and Fog Volume** > **Visual Environment** > **Sky Type** (例如 `PhysicallyBasedSky`, `HDRI Sky` 等)。
        
    - **Lighting Window** > **Environment** 中的環境光設定。
        
    - 場景中烘焙的 **Light Probes** 和 **Reflection Probes**。
        

---

### 總結圖

程式碼片段

```
graph TD
    subgraph Unity Editor
        A[Fog Attenuation Distance] --> C{meanFreePath};
        B[Albedo] --> C;
        D[Anisotropy] --> E{anisotropy};
        F[Scene Lights] --> G[Light Datas];
        H[Sky & GI] --> I[Probe Datas];
    end

    subgraph C# Scripts
        C --> J[_HeightFogBaseExtinction];
        C --> K[_HeightFogBaseScattering];
        E --> L[_GlobalFogAnisotropy];
        G --> M[_LightDatas];
        I --> N[_VolumetricAmbientProbeBuffer];
    end

    subgraph GPU Shaders
        J --> O[extinction];
        K --> P[scattering];
        L --> Q[anisotropy];
        M --> R[Direct Light Evaluation];
        N --> S[Probe Evaluation];

        O --> T[opticalDepth] --> U[transmittance];
        Q --> V[phase];
        R --> W[blendValue.rgb];
        S --> X[probeRadiance];

        U & P & V & W & X --> Y[totalRadiance Accumulation];
    end

    Y --> Z[Final Fog Luminance];

```