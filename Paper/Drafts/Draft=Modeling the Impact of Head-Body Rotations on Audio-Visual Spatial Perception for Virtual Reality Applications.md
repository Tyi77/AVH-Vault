---
up:
  - "[[Modeling the Impact of Head-Body Rotations on Audio-Visual Spatial Perception for Virtual Reality Applications]]"
---
# 目的、方法、結論
這篇論文主要探討的是**在虛擬實境 (VR) 環境中，頭部和身體旋轉對音訊-視覺空間感知的影響**。 為了深入了解此現象，研究人員設計了一系列心理物理實驗，觀察參與者在不同頭部運動模式（例如靜止、追蹤和重新定向）下如何定位空間中的音訊和視覺刺激。

論文提出的方法包含以下幾個步驟：

- **測量感知差異：** 讓參與者執行一項雙選迫選任務，判斷音訊刺激相對於視覺刺激的位置（左或右）。透過改變音訊刺激相對於視覺刺激的偏移量，研究人員能夠建立心理測量函數，量化參與者感知音訊-視覺偏差的能力。
- **建立心理測量模型：** 使用邏輯函數擬合參與者的反應數據，生成心理測量曲線。這些曲線提供了兩個重要指標：主觀相等點（PSE，即音訊和視覺刺激被感知為對齊的位置）和檢測閾值（DT，即參與者能夠可靠地檢測到音訊-視覺偏差的最小偏移量）。
- **分析不同觀看模式和旋轉速度的影響：** 研究人員分析了四種不同的觀看模式（靜止、追蹤、快速重新定向和慢速重新定向）以及三種不同的旋轉速度（0°/s、25°/s 和 50°/s）。結果顯示，在頭部相對於視覺刺激靜止的情況下（靜止和追蹤模式），參與者能夠準確地定位音訊刺激。 然而，當頭部相對於視覺刺激旋轉時（重新定向模式），參與者傾向於高估音訊刺激的位置，使其朝向頭部旋轉方向偏移。 此外，隨著旋轉速度的增加，這種感知偏差也會增大。

最終的結論是：**在 VR 環境中，頭部和身體的旋轉會顯著影響音訊-視覺空間感知，導致音訊刺激位置的感知偏差。** 這種偏差在頭部相對於目標物快速旋轉時尤為明顯。 研究結果強調了在設計 VR 內容時，必須考慮到這種感知偏差，以確保使用者體驗的準確性和沉浸感。 例如，開發者可以根據測量到的 PSE 值調整音訊刺激的位置，以補償感知偏差，提高目標定位的準確性。 此外，了解這些感知偏差也能夠幫助內容創作者設計更自然、更逼真的 VR 體驗。
## 問題
1. [[2AFC (two-alternative forced choice)|2AFC: two-alternative forced choice]]
2. 心裡測量函數：量化參與者感知音訊-視覺偏差的能力。
3. 心裡測量曲線
	- 主觀相等點（PSE，即音訊和視覺刺激被感知為對齊的位置)
	- 檢測閾值（DT，即參與者能夠可靠地檢測到音訊-視覺偏差的最小偏移量）
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