- 頭轉的部分 (不同轉速、是否多個聲音刺激) 我就不做了，因為它是在future work中，一定會被他們原本的團隊做走
	- 所以改為專注確認「PSE in Augmented Reality」
## 確認的細節們
- PSE 到底是什麼？用在什麼地方過？
	- 確認PSE的定義
		- 觀察者覺得標準刺激和比較刺激為一致的數值點
		- 探討觀察者在兩個不同的刺激上對於某個參數的一致性。 或某個參數中中間的值。 
			- 比如，物體和聲音在感知位置上的一致。不同臉部表情被判斷成快樂或生氣的中間值
		- 心裡物理學所提出的觀點
		- 通常略為估計為一個區間的中點，或是機率為50%的數值點
	- PSE 過去有應用在哪些領域中？請一一點出
		- 心理物理學 Psychophysics
			- 什麼是心裡物理學？
				- 將抽象的心理，變成實際可測量的學問
	- 有什麼實際的例子？
		- Audio-Visual Spatial Perception, Virtual Reality [[Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception for Virtual Reality Applications|-1-]]
			- 探討在VR中，頭轉時，視覺刺激和聽覺刺激在感知位置上的一致性
			- 在VR裡頭轉時，視覺刺激位置不變，聽覺刺激位置改變，找出在不同的聽覺刺激位置中，讓觀察者感覺視覺刺激和聽覺刺激在同個位置的聽覺刺激位置。那個位置就是此頭旋轉速度下的PSE位置。
			- 頭轉時，將聽覺刺激移到PSE能提升觀察者 Audio-Visual Spatial Perception 的精準度
		- Facial Emotion Perception [-1-](https://osf.io/preprints/psyarxiv/uyvm6_v1)
			- 辨識人臉是開心還是生氣，而開心和生氣機率為一樣的人臉就是 PSE
			- 發現男生的PSE比女生的PSE還偏向開心，也代表中性表情的男性臉會看起來比中性表情的女性臉凶狠
- Modeling 的那些作者使用PSE還有在哪裡？
	- VR中，虛擬世界的頭部位移量乘上一個Gain值，找出特定的Gain值使得觀察者覺得現實和虛擬的頭部位移量並沒有差別