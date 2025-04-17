## Particle System 的設定
- Start Lifetime: 霧氣維持的長度
- Start Speed: 顆粒噴發速度
- Simulation Speed: 顆粒移動速度
- Shape/Scale: 霧氣影響範圍
- Color Over Lifetime/ : 霧氣從開始到結尾的顏色變化
- Renderer/Min|Max Particle Size: 霧氣顆粒大小
## Volume-Fog
- 是 **Height Fog** 不是 平面距離的 Fog
- **Fog Attenuation Distance**: 控制霧的基礎密度，決定了透過霧**可以看到的距離**（以公尺為單位）。在此距離處，霧已吸收並散射63% 的背景光。
- **Base Height**: 在這個高度之前是constant，之後是exponential 的霧氣
- **Maximum Height**: 控制高度霧的衰減率（以公尺為單位）。較高的值會垂直拉伸霧效。在此高度，衰減使初始基礎密度降低63%。
- **Max Fog Distance**: 霧效應用在 Sky Box 或 Background 的距離。**一定要大於 Camera 的 Clipping Planes 的 Far 參數。**
- 