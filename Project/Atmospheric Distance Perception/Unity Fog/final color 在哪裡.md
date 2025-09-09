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


---
`ShaderPassForward.hlsl -> `EvaluateAtmosphericScattering()`

| 參數名稱 | 類型 | 描述 |
| :--- | :--- | :--- |
| renderGraph | RenderGraph | Render Graph 系統的實例，用於排程和執行此渲染通道。 |
| hdCamera | HDCamera | 當前正在渲染的攝影機。它提供了所有攝影機相關的資訊，如視圖/投影矩陣、畫面設定 (Frame Settings) 和螢幕尺寸。 |
| colorBuffer | TextureHandle | 主顏色緩衝區。這是此通道的主要輸入與輸出目標，包含了在它之前已經渲染好的不透明物體顏色。 | 
| depthTexture | TextureHandle | 深度紋理。包含了場景的深度資訊，用於在 Shader 中重建每個像素的世界座標。 | 
| volumetricLighting | TextureHandle | 體積光照緩衝區。這是一個 3D 紋理 (V-Buffer)，儲存了由 VolumetricLightingPass 計算出的、在空間中每個點的光照和散射資訊。這是霧效果的主要資料來源。 | 
| depthBuffer | TextureHandle | 硬體深度/模板緩衝區。用於深度測試，確保霧效果只在現有幾何體上渲染。 |
