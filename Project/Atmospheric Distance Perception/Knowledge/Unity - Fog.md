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
- public **MinFloatParameter**(float value, float min, bool overrideState = false)

