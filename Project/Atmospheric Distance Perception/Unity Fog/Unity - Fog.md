---
up:
  - "[[Knowledge List]]"
tags:
  - Knowledge
---
## 定義
- 整理Unity中對於Fog的相關文件
---
## Volume - Fog 的參數
- **Volumetric Fog Distance** : 決定有三維格點的frustrum大小，以控制霧氣的品質（越遠frustrum越大品質就越低）
- **Base Hight** : 以下：均值霧(constant/homogeneous fog)；以上：exponential Fog
- **Fog Attenuation Distance**: Controls the global density of the fog.
- **Maximum Height**: Controls the density falloff with height; allows you to have a greater density near the ground and a lower density higher up.
## 其他資料
- [SIGGRAPH 2014 Ubisoft簡報](https://advances.realtimerendering.com/s2014/#_VOLUMETRIC_FOG:_UNIFIED)
## 數學公式程式來源
- **Fog override**
	- D:\77Unity\Lab\Project\2022-3-HDRP\Library\PackageCache\com.unity.render-pipelines.high-definition@14.0.12\Runtime\Lighting\AtmosphericScattering\ **Fog.cs**
#### Fog Attenuation Distance 的發掘過程
- Fog Attenuation Distance 是 Mean Free Path 
	```csharp
// Fog.cs
/// <summary>Fog mean free path.</summary>
[DisplayInfo(name = "Fog Attenuation Distance")]
public MinFloatParameter meanFreePath = new MinFloatParameter(400.0f, 1.0f);
```
- 將meanFreePath和其他參數（albedo, anisotropy）封裝起來
	```csharp
// Fog.cs
LocalVolumetricFogArtistParameters param = new LocalVolumetricFogArtistParameters(albedo.value, meanFreePath.value, anisotropy.value);
```
- 把meanFreePath放進struct中（也就是前面的param），然後再變成extinction
	```csharp
// LocalVolumetricFog.cs
public partial struct LocalVolumetricFogArtistParameters {
	...
	/// <summary>Mean free path, in meters: [1, inf].</summary>
	public float meanFreePath; // Should be chromatic - this is an optimization!
	...
	public LocalVolumetricFogArtistParameters(Color color, float _meanFreePath, float _anisotropy) {
		meanFreePath = _meanFreePath; // Tyi77: Set the parameter.
	}
	...
}
...
internal LocalVolumetricFogEngineData ConvertToEngineData()
{
	LocalVolumetricFogEngineData data = new LocalVolumetricFogEngineData();

	data.extinction = VolumeRenderingUtils.ExtinctionFromMeanFreePath(meanFreePath);
...
}

// HDRenderPipeline.VolumetricLighting.cs
	public static float ExtinctionFromMeanFreePath(float meanFreePath)
	{
		return 1.0f / meanFreePath;
	}
	public static Vector3 ScatteringFromExtinctionAndAlbedo(float extinction, Vector3 albedo)
	{
		return extinction * albedo;
	}
```

