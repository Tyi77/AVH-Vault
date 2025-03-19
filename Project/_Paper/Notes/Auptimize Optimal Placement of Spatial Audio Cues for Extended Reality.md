---
up:
  - "[[Project/_Paper/Maps/Paper List]]"
date: 2024-12
publication: UIST
p-date: 2024-10
tags:
  - Paper
  - "#Paper-Deep"
---
## 重點分析
看到的問題點
* 因為人身體的限制，我們本來就很難精確定位聲音來源。有的問題，譬如localization blur和cone of confusion。
* 解釋ITD、ILD
    * ITD: It is the difference in the sound arrival time of each ear.
    * ILD: It is the difference in the volume of the sound heard by each ear.
* 再解釋兩個問題
解法：建構一個系統，偵測目前的聲音提示，並優化和移動聲音的位置，讓使用者能更清楚的區分不同聲音提示的位置

資料集
* 來源：自己收集，
* 偵測人們預測的結果：紫色、橘色、視覺和聽覺要分開

## 可以延伸的內容
* the phenomenon of binaural unmasking

## 論文筆記
**Introduction**
這篇研究提出了名為 Auptimize 的新穎計算方法，旨在改善擴增實境 (XR) 中空間音訊提示的放置，以減少使用者因為聽覺感知限制而造成的錯誤。
* Auptimize 利用「腹語效應」，將聲音來源位置與其對應的視覺元素分離，並將它們重新定位到最佳位置，以最大程度地減少混淆。
* 人類聽覺系統的限制，例如定位模糊和前後混淆，空間音訊提示容易出錯
* Auptimize 包含兩個主要元件：分析器和最佳化器。
* 研究透過使用者研究評估了 Auptimize，發現與在配對視聽位置播放聲音提示相比，Auptimize 減少了基**於空間音訊的來源識別錯誤。

---

**BACKGROUND AND RELATED WORK**
1. 人類如何定位聲音
* ITD, ILD
* 前後混淆和定位模糊
2. 腹語效應
3. 數位系統中的定位
* 模擬ITD, ILD, HRTF的做法
4. 互動式系統的空間音訊

===

Data collection

收集

播放一段白噪音的聲音，使用者看向那個聲音並按下頭盔上的按鈕，以紀錄使用者些看向的方向
距離使用者1.5m
分析

重點：方位角誤差
front-back confusion
難區分前後的聲音，因為ITD很像
cone of confusion
難區分同個cone上的聲音，因為ITD、ILD很像
以confusion matrix形式呈現
紫色：localization blur的影響
前後側比左右側明顯，因為斜角線前後側發散的比較多
橘色： cone of confusion + localization blur
前後側比左右側明顯
最好的分數不一定在對角線上，所以把視覺和聽覺資訊分開是對的。
(但我覺得或許是裝置壞掉或校準不精確的問題)

---

Results

Accuracy (GLMM)

method as fixed effect

Auptimize > HRTF : moderate effect size
Auptimize > dynamic audio : strong effect size
method & visibility as fixed effect

Auptimize > HRTF : 但只有些微的變好
Auptimize > dynamic audio 在 visible condition : 有實質上的變好
但在 hidden condition中沒有顯著的變好
Response Time (ANOVA)

Auptimize 和 dynamic audio
顯著性不一樣 (***)
medium effect size
Hidden < Visible : 代表東西看不見時，使用者回應的較快
在同個visibility的狀況下比較時 (Visible 或 Hidden)
Auptimize < HRTF < dynamic

---

User Evaluation

180 次試驗的計算方式如下：

三種方法 (Generic HRTF, Dynamic Audio, Auptimize)
兩種可見性級別 (可見, 隱藏)
三種佈局類型 (side-by-side, cone of confusion, random)
五次試驗 (每個佈局類型中，目標元素被隨機選擇五次)
兩次重複 (每個區塊重複兩次)
因此，每個區塊的試驗次數為 3 x 2 x 3 x 5 = 90 次試驗。 由於研究分為兩個區塊，所以總共的試驗次數為 90 x 2 = 180 次試驗。

---
Discussion

Relationship between Auptimize and HRTF
further evaluation in diverse setups is needed to test the scalability of our approach.