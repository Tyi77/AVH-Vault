## 總覽
- Unity要用哪個版本 (==最後確定要使用 2022.3 HDRP==)
	- URP
		- 2020.3 - 已經有fog的實作只是要看裡面的參數在物理意義上代表什麼
		- 2022 - 在VR上的支援可能比2020的還多
		- ~~Unity6 - 最新的Unity版本~~ (決定不用這個版本，還不太穩定)
	- HDRP
		- 有現成的 Fog Volume Shader 可用
			- 但問題是 Quest 3 是 Stand alone 的 VR，效能限制無法使用 HDRP
				- 但有機會是在 PC 上跑遊戲，但是以Streaming的方式在 quest 3 上顯現
			- 或是改為用實驗室中舊版的 HTC Vive Pro 或 HTC Vive Cosmos Elite
## Sky Box
- 我覺得可以使用 ==Physical Sky Box== 以真實的模擬自然界天空的場景
- Physical Sky Box 的設置
	- 原本的，不用勾選override
- Cloud 的設置
	- 關閉 Cloud layer
## Fog的實作
> [2020.3社群的實作](https://www.reddit.com/r/Unity3D/comments/rioi8d/released_a_free_pseudovolumetric_textureless/?utm_source=chatgpt.com)
- 在真實世界中會影響 Fog 的參數
	- 濕度、氣壓、氣溫、地形、風速、凝結核
- 相關參數
	- Fog本身
		- **能見度(Visibility)**
			- 能清楚見到的距離 (Fog Attenuation Distance)
				- Attenuation Length 在物理上的定義為光的強度衰減至原本強度的 1/e 時所需要的距離。此強度大約是36.8%，而被吸收的強度大約是63.2%。
				- 此參數的設計照著這樣的定義
		- **顆粒的顏色(Color)**
			- Color Mode - Sky Color
			- Volumetric Fog
				- Albedo - Change the color here
	- Light Source
		- **光的強度：Day/Night**
			- 照著 Physical Sky Box 的設置
- ==Fog的話，因為重力，所以靠近地面的地方會比較濃厚，靠近天空會比較淡==
#### 濕度
- 濕度是怎麼做計算的？
	- **絕對濕度**：是指每單位體積空氣中水汽的質量，通常以克/立方米(g/m3)作單位，反映空氣的實際水汽量。
	- **相對濕度**：是指空氣中的實際水汽壓與在相同溫度下飽和水汽壓的比例，通常以百分比(%)表達。
- Unity有辦法精確到說我濕度數值多少，分別代表哪個數值多少嗎？
	- 不行，頂多做能見度的計算
- 那有辦法把濕度對應到能見度的數值嗎？
	- Unity那個是過了
#### 論文閱讀
- Why fog increases the perceived speed
	- Fog是用一個decrease數學模型模擬出來的
	- 這個明天再來仔細看
- ==Babu老師的論文==
	- 跟測量方法有
## Rain的實作
- 相關參數
	- droplit size、speed
- water
	- Jerry tesendor
## Smoke的實作