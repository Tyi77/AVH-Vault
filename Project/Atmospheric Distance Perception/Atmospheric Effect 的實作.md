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
- 我覺得可以使用 Physical Sky Box 以真實的模擬自然界天空的場景
- Physical Sky Box 的設置
- Cloud 的設置
## Fog的實作
> [2020.3社群的實作](https://www.reddit.com/r/Unity3D/comments/rioi8d/released_a_free_pseudovolumetric_textureless/?utm_source=chatgpt.com)
- Fog 在真實物理意義上對應的遊戲參數
	- 濕度：
	- 濃度/可見度/可透光度：
	- 流動速度：
- 相關參數
	- Fog本身
		- 能見度(Visibility)
			- 能清楚見到的距離 (Fog Attenuation Distance)
		- 顆粒的顏色(Color)
			- Color Mode - Tint
	- Light Source
		- 光的強度：Day/Night
#### 論文閱讀
- Why fog increases the perceived speed
	- Fog是用一個decrease數學模型模擬出來的
	- 這個明天再來仔細看
## Rain的實作
- 相關參數
	- droplit size、speed
- water
	- Jerry tesendor
## Smoke的實作