> [[Simulation of Atmospheric Visibility Impairment]]
## Main Point
- **Motivation** – Existing fog/haze datasets are limited in physical fidelity, diversity and scale, thus insufficient for modern CV models that must cope with visibility degradation.
- **Optical foundation** – Derive dedicated scattering/absorption models for five common phenomena (Mist, Homogeneous Fog, Heterogeneous Fog, Natural Haze, Smog, Asian Dust) under the constraints of _Koschmieder_ and _Duntley_ laws.
- **Data acquisition** – Extract **40 k photorealistic clear images + depth maps** from GTA V via RenderDoc / ScriptHook. Apply the above models to synthesize **800 k degraded images** and release the **AVID** dataset.
## Related Work
- jkj
## 兩個公式的介紹
- Koschmieder, Duntley laws
## 解構不同的效應
- Mist
- Fog
- Natural Haze
- Smog
- Asian Dust
## Analysis
- 客觀的圖片
- 主觀的圖片
## Feedback
- 這個方法可能不適用於3D的場景
- Fog是不會動的
- motion parallax
- 要看看是否只有符合360 video