# Main Thought
- 原本論文 [[Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception for Virtual Reality Applications|-1-]]
- 原本的論文是轉頭的時候，固定==物體聲音==的旋轉速率，而我希望==物體聲音==的旋轉速率可以隨時因應==轉頭的速率==而調整
- 目的是讓物體聲音一直都在 ==PSE (Point of Subjective Equality)== 上
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
# Comprehensive Proposal
## Main Idea
## Study Design
- Hypothesis
## Experiment Design
## Analysis Method
## Conclusion