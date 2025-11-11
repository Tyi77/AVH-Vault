## Depth perception in virtual reality: The impact of spatial interaction and color-based cues
### 2. Related Work
#### 2-2
- 深度感知問題在很多task上是很重要的因此需要被解決。有人嘗試用color的方式來嘗試，譬如 chromadepth 或 pseudo-chromadepth 的方式，hue map to depth。對比度(誇大差距)或透明度也能改變深度感知。
#### 2-3
- CIELAB是最符合人類顏色感知的色彩空間，也常被心理學研究使用
### 3. Evaluation of the different perception depth in VR
#### 3.2 Result Analysis
- Accuracy有三個指標：Depth length error, spatial dimension bias, UI interaction issues
- Depth length error
	- standardized residuals
	- Z軸誤差明顯高於XY軸誤差，有80%的參與者在深度軸上出現明顯誤差。
	- 他們讓受試者在同樣的形狀重繪三次，以確保是 perceptual compression 的問題，而不是 motor control inaccuracy 所造成的影響。
	- 其他統計結果
		- 性別對深度誤差沒有顯著影響。
		- 但VR使用經驗與誤差率呈顯著負相關。換句話說，**VR經驗越多的參與者，其深度知覺誤差越小。**
- Spatial dimension bias
	- Z軸縮短最多
	- 實際體積大小與繪製體積大小沒有顯著差異。代表大小還算準確，只是延伸感出了問題