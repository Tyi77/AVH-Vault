# Main Thought
- 原本論文 [[Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception for Virtual Reality Applications|-1-]]
- 原本的論文是轉頭的時候，固定==物體聲音==的旋轉速率，而我希望==物體聲音==的旋轉速率可以隨時因應==轉頭的速率==而調整
- 目的是讓物體聲音一直都在 ==PSE (Point of Subjective Equality)== 上
# Secondary Idea
- 兩個不同的物體要怎麼做分析
# 不同情境
![[Pasted image 20250201194926.png]]
- Stationary 不適用，因為 PSE 就是 0° 的地方
- Pursuit 的設定是人跟隨著物體。物體和人都會旋轉，所以可以試試看找此兩因素相應的相對速率的PSE
- Slow/fast re-orientation 只有人會旋轉。PSE只要考慮人旋轉這個因素就行
# 準備閱讀的論文
- [Using the standard staircase to measure the point of subjective equality: A guide based on computer simulations](https://link.springer.com/content/pdf/10.3758/BF03213053.pdf)
	- PSE有關的舊的論文
	- 結論：不用看，因為此論文著重探討兩種與PSE相關的心理物理學分析方法，而不是PSE本身
- [Disguising Rotational Gain for Redirected Walking in Virtual Reality: Effect of Visual Density](https://ieeexplore.ieee.org/abstract/document/7504752/) (2016 VR)
	- 使用者旋轉速率和虛擬人物旋轉速率不一致，用rotation gain調整兩者的關係，gain值
	- 88 trials = 11 gain levels x 2 turning directions x 4 scenarios
		- scenarios: control(bridge), 0, 4, 16 objects
	- Use an pre-process to filter out the participants who feel uncomfortable with VR experience.
	- 問題：如何使用PSE在他的work中
		- 回答：他用PSE的位置，偵測使用者感受 rotation gain 的狀況。結論是如果環境中有很多物品的話，會讓使用者覺得rotation gain變小了，也就是感知的旋轉幅度會比真正的旋轉幅度來的小。
# Q & A
- 如果物體在不同的azimuth，是否會有不同的 PSE ?
# Comprehensive Proposal
## Main Idea
- Adjust PSE dynamically when participants turning the head.
## Inspiration
- modeling ... : turning head
- auptimize ... : multiple visual stimuli candidate.
## Study Design I
- Calculate Different PSE in Different Head Turning Velocity and Different Azimuths.
- All are re-orientation
- Metric
	- confusion metric
	- response time
## Study Design II
- Multiple visual and multiple auditory stimuli with different head turning velocities
- Method
	- Determine different locations of PSE basing on the location of different objects and different head turning velocities of the user.
## Experiment Design
- 
## Analysis Method
## Conclusion
# 打預防針的解釋
- In the last meeting, I proposed an idea about comparing the difference between a single PSE shift and dynamically shifting the PSE. However, I realized that this approach is more engineering-oriented rather than an academic perspective. Therefore, I would like to read more papers to explore new ideas.
- application 中有一段有說到，受試者的頭轉平均速率是115，而他們使用之前測量到的50的結果拿來當作PSE的位置。因此或許就算在實驗上增加了比50更高的速率的討論，有可能其結果跟50的結果的差距微乎其微