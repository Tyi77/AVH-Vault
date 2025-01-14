---
up:
  - "[[Paper List]]"
date: 2025-01
tags:
  - Paper
publication: IEEE TVCG
p-date: 2024-05
---
# Draft
[[Draft=Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception for Virtual Reality Applications]]
# Linked Paper/Knowledge
* multimodal sensory feedback
	* **External** (mainly visual and auditory)  
		- J. Prinz. Is the mind really modular. [[Contemporary Debates in Cognitive Science]], 14:22–36, 2006  
	* **Internal** (balance and body position awareness)  
		- L. Shams and R. Kim. [[Crossmodal influences on visual perception]]. Physics of Life Reviews, 7(3):269–284, 2010.
* **rapid head movements** introduce **ballistic changes** on the retina, which in turn leads to a degradation of the perceived auditory space
	- J. Leung, D. Alais, and S. Carlile. [[Compression of auditory space during rapid head turns]]. Proc. Nat. Acad. Sci. U. S. A., 105(17):6492–6497, 2008.
- Spatial Localization Acuity
	- Previous studies on sound localization acuity demonstrate outstanding precision in discerning sounds with horizontal spatial separations of  over 3◦ [14, 31].
- M. Kytö, K. Kusumoto, and P. Oittinen. [[The ventriloquist effect in augmented reality]]. In IEEE International Symposium on Mixed and Augmented Reality, pp. 49–53, 2015.
- Previous Work
	- A. Serrano, D. Martin, D. Gutierrez, K. Myszkowski, and B. Masia. [[Imperceptible manipulation of lateral camera motion for improved virtual reality applications]] ACM Trans. on Graph., 39(6), 2020.
		- Lateral camera motion
# Key Idea
* **虛擬實境 (VR)** 環境中，**頭部和身體旋轉** 對 **音訊-視覺空間感知** 
* Sound Localization Acuity
* [[Psychophysics]]
* [[Psychometric Function]]
* Shift the audio stimuli to PSE, to make user perceive the correct visual stimuli.
	* PSE (Point of subjective equality): The location that user perceive the visual and auditory stimuli are aligned.
# What I learned
---
# Q&A
## PSE和rotation direction/velocity的關係
![[Pasted image 20250109234409.png]]
- PSE偏移方向會背對旋轉方向 (往右轉，PSE往左偏移)
- 靜止的較不偏移，旋轉的偏移較大
- 旋轉越快，偏移越大
---
# Introduction
- We explore four headbody movements **(Stationary, Pursuit and Slow/Fast re-orientation)** and  different **audio-visual offsets.**
- When the head is aligned relative to the visual stimulus (Stationary and Pursuit), users exhibit a **high degree of sensitivity** in discerning misalignments between auditory and visual cues.
- when there is relative motion between the head and the visual stimulus (Re-orientation mode), our ability to detect audio-visual offsets is **notably compromised**
- Some applications
	- VR storytelling
	- training and simulation
# Related Work
- Sound Localization Acuity
	- head movements contribute to improved spatial localization [13].
# 實驗流程
- 四種不同的實驗方式：static, pursuit, fast和slow re-orientation
- 使用者感知視覺和聽覺刺激兩秒後，要說聲音是從左方還是右方來的，只能二選一(2AFC)
- 用psychometric function fit 資料點