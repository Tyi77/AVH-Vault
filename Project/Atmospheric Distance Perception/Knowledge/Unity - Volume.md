---
up:
  - "[[Knowledge List]]"
tags:
  - Knowledge
---
## Visual Environments
> [文件](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@14.0/manual/Override-Visual-Environment.html)
- Sky type 選好後記得要加上相對應的 override
- Wind 中的參數只是設定而已，需要連上其他的物件才能真正使用這些參數
	- 讓Cloud使用Wind參數：加上 `Volumetric Clouds` override ，勾選Wind底下的兩個參數，並設置為 `Global`，這樣clouds就會依照Visual Environments中的Wind設定來設定自己的Wind參數
## Physical Based Sky
> [文件](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@14.0/manual/Override-Physically-Based-Sky.html)
- The Physically Based Sky’s atmosphere has two types of particles:
	- Air particles with [Rayleigh scattering](https://en.wikipedia.org/wiki/Rayleigh_scattering).
	- Aerosol particles with anisotropic [Mie scattering](https://en.wikipedia.org/wiki/Mie_scattering). You can use aerosols to model pollution, height fog, or mist.
- Space放上star maps後就可以模擬夜晚的星星