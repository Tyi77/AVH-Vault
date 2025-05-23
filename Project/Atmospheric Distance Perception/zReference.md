## Paper
### Atmospheric Effect
- https://dl.acm.org/doi/10.1145/3385955.3407933
	- 實驗場景
		- 使用者可以看到自己真實的身體，而環境為綠幕製成的虛擬山谷
		- **3 種目標物**（紅色圓柱體 1.51m、高約 1.79m 的男性人形 avatar、橘色長方柱體 3m）
		- **7 個可能距離**：25、50、100、200、300、400、500 公尺
	- 兩個主效果
		- 距離：近距離高估(200m以內)，遠距離低估(200m以外)
		- 高低：目標越高越低估，越低越高估
	- 兩個主效果的交互作用 (post-hoc)
		- 近距離 (25m, 50m)
			- 在**近距離**時，不同**高度**物體的距離估計才有顯著差異
				- 大物體的距離會被低估(長方柱體)，小物體的距離會被高估(圓柱體+人形)
		- 遠距離 (100m 和以上)
			- 在遠距離，不同物體之間的距離感知沒有顯著差異
				- 物體高低跟距離感知沒甚麼太大的關係
	- 人形目標(avatar)會導致：高估
		- 因為人形的身高或樣態是人們比較熟悉的，因此就像真實中看相遠方的路人一樣，會覺得對方比較遠
	- **量度方式的理解**
	- 他為什麼要有參考物
- Volume Rendering的資料(Prof. Lin給的)
	-  [https://advances.realtimerendering.com/s2014/#_VOLUMETRIC_FOG:_UNIFIED](https://advances.realtimerendering.com/s2014/#_VOLUMETRIC_FOG:_UNIFIED "https://advances.realtimerendering.com/s2014/#_volumetric_fog:_unified")  
	- [https://github.com/Unity-Technologies/VolumetricLighting/blob/master/Assets/VolumetricFog/Shaders/Scatter.compute](https://github.com/Unity-Technologies/VolumetricLighting/blob/master/Assets/VolumetricFog/Shaders/Scatter.compute "https://github.com/unity-technologies/volumetriclighting/blob/master/assets/volumetricfog/shaders/scatter.compute")
	- [https://www.ea.com/frostbite/news/physically-based-unified-volumetric-rendering-in-frostbite](https://www.ea.com/frostbite/news/physically-based-unified-volumetric-rendering-in-frostbite "https://www.ea.com/frostbite/news/physically-based-unified-volumetric-rendering-in-frostbite")
### Distance Measurement Method
- [Distance perception in real and virtual environments](https://dl.acm.org/doi/abs/10.1145/1077399.1077402)
- [Methods for measuring egocentric distance perception in visual modality](https://www.frontiersin.org/journals/psychology/articles/10.3389/fpsyg.2022.1061917/full)
