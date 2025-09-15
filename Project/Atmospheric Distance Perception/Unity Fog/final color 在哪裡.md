- final color 在哪裡?
	- `AtmosphericScattering.hlsl` `EvaluateAtmosphericScattering`
## 1. 把 Fog 相關參數打包進`ShaderVariablesGlobal cb` 中
- `HDRenderPipeline.cs` 裡面的內容，直到`Fog.UpdateShaderVariablesGlobalCB()`
	- `HDRenderPipeline.cs/Render()`->**ExecuteAOVRenderRequests()**->ExecuteRenderRequest()->UpdateGlobalConstantBuffers()->UpdateShaderVariablesGlobalCB()->Fog.UpdateShaderVariablesGlobalCB()
	- `HDRenderPipeline.cs/Render()`->ExecuteRenderRequest()->UpdateGlobalConstantBuffers()->UpdateShaderVariablesGlobalCB()->Fog.UpdateShaderVariablesGlobalCB()
- `Fog.cs/UpdateShaderVariablesGlobalCB()` -> fogSettings.UpdateShaderVariablesGlobalCBFogParameters(ref cb, hdCamera);
	- 把參數打包進`ShaderVariablesGlobal cb` 中
## 2. .shader 使用打包好的參數
- `HDRenderPipeline.cs/ExecuteRenderRequest()` -> `HDRenderPipeline.RenderGraph.cs/ExecuteWithRenderGraph()` -> RecordRenderGraph() -> `SkyManager.cs/RenderOpaqueAtmosphericScattering()` -> `HDUtils.cs/DrawFullScreen()`
	- 在call DrawFullScreen()時就會傳特定的shaderPassId過去了
	- 之後就會進到GPU端做運算，並以這些參數執行特定的Shader
- `OpaqueAtmosphericScattering.shader/Frag()|FragMSAA()|FragPBRFog()|FragMSAAPBRFog()` -> AtmosphericScatteringCompute() -> `AtmosphericScattering.hlsl/EvaluateAtmosphericScattering()`
	- `OpaqueAtmosphericScattering.shader` 一定會被呼叫到。如果場景中沒有物體，那就會以天空為物體，深度資訊就會是無窮遠，而此相關函數可以處理無窮遠這種特例的情況。
	- 不同的Frag() Function 是依據是否有MSAA和PBR來分的。目前一定沒有PBR，因為Unity還沒Implement出來。而MSAA需要硬體資源再開才好。因此目前設定是沒有MSAA和PBR的純 Frag() Function。
## 3. `EvaluateAtmosphericScattering()` 裡在做什麼？
- `fogFragDist`: 目標與camera的直線距離
- 如果 Fog Override 有被啟用，執行以下程式碼
	- `volFog`: 計算後的顏色
	- `expFogStart`: 它儲存了 V-Buffer 所能及的最遠距離。所有超出這個距離的像素，都需要用下面的「遠處霧」來補足
	- 如果 Volumetric Fog 有被啟用，執行以下程式碼
		- SampleVBuffer(): 重點function，建造Height Fog 的核心funtion
		- DelinearizeRGBA(): 把線性顏色值轉換回顯示用的顏色空間
	- 如果 `distDelta > 0` (i.e. 像素的距離超出了體積霧的範圍`expFogStart`)
### 整理資訊
- 如果Volumetric Fog沒有被啟用的話，因為`expFogStart`都會是0，所以一定會執行fall back的那段程式碼。
## 4. `SampleVBuffer()`

| 參數名稱                     | 類型                      | 描述                                            |
| ------------------------ | ----------------------- | --------------------------------------------- |
| TEXTURE3D_ARGS(tex, smp) | Texture3D, SamplerState | 要取樣的 3D 體積紋理 (_VBufferLighting) 及其取樣器狀態。      |
| positionNDC              | float4                  | 螢幕空間的正規化裝置座標 (Normalized Device Coordinates)。 |
| viewDist                 | float                   | 視點到片元的距離。                                     |
| viewportSize             | float4                  | 包含 VBuffer 檢視區大小資訊 (寬、高、寬的倒數、高的倒數)。           |
| viewportScale            | float3                  | VBuffer 檢視區的縮放比例。                             |
| viewportLimit            | float3                  | VBuffer 檢視區的邊界限制。                             |
| distanceEncodingParams   | float4                  | 用於將線性距離編碼為非線性 VBuffer 深度的參數。                  |
| distanceDecodingParams   | float4                  | 用於將 VBuffer 深度解碼回線性距離的參數。                     |
| useTrilinear             | bool                    | 是否使用三線性過濾。                                    |
| useBicubic               | bool                    | 是否使用雙三次方過濾進行重建。                               |
| useAnisotropy            | bool                    | 是否考慮非等向性散射。                                   |

---
---
`ShaderPassForward.hlsl -> `EvaluateAtmosphericScattering()`

| 參數名稱               | 類型            | 描述                                                                                           |     |
| :----------------- | :------------ | :------------------------------------------------------------------------------------------- | --- |
| renderGraph        | RenderGraph   | Render Graph 系統的實例，用於排程和執行此渲染通道。                                                             |     |
| hdCamera           | HDCamera      | 當前正在渲染的攝影機。它提供了所有攝影機相關的資訊，如視圖/投影矩陣、畫面設定 (Frame Settings) 和螢幕尺寸。                              |     |
| colorBuffer        | TextureHandle | 主顏色緩衝區。這是此通道的主要輸入與輸出目標，包含了在它之前已經渲染好的不透明物體顏色。                                                 |     |
| depthTexture       | TextureHandle | 深度紋理。包含了場景的深度資訊，用於在 Shader 中重建每個像素的世界座標。                                                     |     |
| volumetricLighting | TextureHandle | 體積光照緩衝區。這是一個 3D 紋理 (V-Buffer)，儲存了由 VolumetricLightingPass 計算出的、在空間中每個點的光照和散射資訊。這是霧效果的主要資料來源。 |     |
| depthBuffer        | TextureHandle | 硬體深度/模板緩衝區。用於深度測試，確保霧效果只在現有幾何體上渲染。                                                           |     |
