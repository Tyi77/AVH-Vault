---
up:
  - "[[Paper/Maps/Paper List]]"
date: 2025-03
publication: IEEE TVCG
p-date: 2023-05
tags:
  - Paper
---
# Draft
# Linked Paper
# Knowledge
# Key Idea
# What I learned
# Q&A
---
## Introduction
- Natural Freehand Gestures
- Proteus Effect
## 2. Related Work
### 2.1 Interaction
- natural > non-natural
	- But some papers get the inverse conclusion
- gestures
- far-field interactions
	- multi-modal interaction technology are introduced here
	- Challenges of freehand gestures in far-field interactions
- metaphoric(隱喻) vs isomorphic(同構的、相同形式的)
### 2.2 Effects of Avatars
- Display Devices, Redering Technique, User Perspective.
- Avatar from pure virtual to pure physical.
- more muscular avatar, users physical performance improves
- end-effector
	- Simple end-effector can speed up task completion
### Impact of Real Hand Visibility
- The visibility of the real hand
	- As the visibility of the vitural hand increases, the visibility of the real hand decreases.
## 3. SYSTEM DESCRIPTION
### 3.3 Hand Representations
- 無avatar，象徵式avatar(骨架)，整手部的avatar
### 3.4 Virtual Light Intensity
- 高低強度虛擬光源會影響真實手部的可見度，並會影響使用者與全息影像的互動
- 所有光源都是白色且強度都是一，強度高低差別只差在光源數量，低強度為光源數量為2，高強度為光源數量為5
## 4. EXPERIMENT
- 我們採用了 3（增強手部表示）×2（障礙物密度）×2（障礙物大小）×2（虛擬光強度）的多因素設計
	- 跨組別因素：不同使用者組別用不同的增強手部表示
	- 每個條件下都要做 20 次試驗
		- 所以每個使用者要做 160 = 2 x 2 x 2 x 20 次試驗 (不用 x 3 因為增強手部表示是跨組別的因素)
- Hypothesis
	- augmented avatar > no augmented avatar
	- 高密度會導致低表現
	- 障礙物大小會影響表現
	- 高虛擬光強度會導致低表現
	- 較深的目標會導致低表現