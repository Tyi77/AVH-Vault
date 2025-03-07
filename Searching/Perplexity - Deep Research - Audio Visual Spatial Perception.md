### **虛擬、增強與混合現實中的音視覺空間感知：關鍵概念、最新進展與未來方向**

整合聽覺與視覺刺激於空間環境中，是沉浸式技術中感知體驗的核心。虛擬、增強與混合現實（VR/AR/MR）中的音視覺空間感知，涉及人類感官系統與技術應用之間的複雜交互，旨在創造逼真的多感官體驗。最新研究表明，人類在 VR 環境中對音視覺空間偏移的敏感度高於以往認知，突顯了精確的多感官對齊對於沉浸式體驗的重要性[1]。該領域正在快速發展，神經學研究與技術實作的進步持續提升虛擬環境的互動體驗。本報告將探討沉浸式技術中音視覺空間感知的關鍵概念，總結近期研究進展，並闡述該跨學科領域未來的研究方向。

---

## **音視覺空間感知的基本原理**

音視覺空間感知指的是人類如何在三維空間中感知和整合聽覺與視覺信息。在 VR、AR 和 MR 環境中，這種感知整合對於創造逼真的體驗至關重要。人類的感知系統會自然而然地結合多重感官信息，以形成對環境的完整理解，其中視覺與聽覺在空間感知方面尤為重要[3]。這種跨感官整合並非簡單的訊息疊加，而是涉及複雜的神經機制，可根據感官信息的一致性與可靠性來增強或抑制特定的感官信號。

「腹語效應」（ventriloquism effect）是這種整合的典型例子，即人類會將聲音來源錯誤地歸因於與其同時發生的視覺刺激[10]。該現象對於沉浸式環境的設計有著重要影響，表明音視覺空間的對齊不必完全精確，仍可提供令人信服的體驗。研究顯示，在 AR 環境中，可利用這一效應來補償音頻空間化的技術限制[7]。然而，使用者對於可接受的空間誤差範圍，會受到環境、使用者預期和具體應用場景的影響。

時間同步性（temporal synchrony）亦是影響空間感知的關鍵因素。研究發現，音視覺不同步會顯著影響使用者在沉浸式媒體中的臨場感[5]。人類感知系統對於時間上的不匹配有一定的容忍度，但超過該範圍將破壞沉浸感，降低體驗品質。理解這些時間整合窗口，對於 VR、AR 和 MR 平台內容的開發至關重要。

「自適應多感官整合」（Adaptive Multi-sensory Integration）在沉浸式技術中變得愈發重要。該概念指的是人類能夠適應新的感官關聯，在虛擬環境中重新校準聽覺與視覺信息的整合方式[4]。這種適應性使得使用者可以逐步調整至可能異於現實的感官映射，但適應的程度與速度會因個人及情境而異。

---

## **技術實作與挑戰**

在沉浸式環境中創造逼真的音視覺空間體驗，需要精細的技術實作。視覺部分涉及考量深度線索、立體視覺與透視關係的渲染技術；聽覺部分則依賴於「頭部相關傳輸函數」（HRTF）、Ambisonics 和基於物件的音頻技術，以創造與使用者動作動態響應的三維音景[9]。這些空間音效技術對於維持虛擬環境的臨場感至關重要。

實現精確的跨模態空間感知仍面臨諸多挑戰。其中之一是如何在三維空間中準確對齊視覺與聽覺刺激。在 AR 環境中，虛擬元素須與現實世界保持對齊，這使得音視覺的空間同步性變得尤為困難[6]。目前 AR 系統的聽覺定位精確度仍不及視覺，可能導致跨模態衝突，影響使用者體驗。

個人化的空間音頻渲染亦是挑戰之一。現有的通用 HRTF 模型未考慮個體解剖結構的差異，而這些差異會影響人們對空間音效的感知。研究表明，個人化的 HRTF 可顯著提升空間音頻的真實感，但其獲取方式通常需要專業設備與耗時的測量過程[9]。近期的計算建模與機器學習技術進展，正在使個人化空間音效變得更易獲取，然而普及應用仍然面臨挑戰。

硬體限制亦影響音視覺空間體驗的品質。目前的 AR 顯示設備通常具有較小的視場（Field of View, FOV），可能導致視覺與聽覺空間感知的不一致，尤其是當聲音來自視野之外時[12]。此外，VR 和 AR 頭戴設備的重量與形態亦影響長時間使用的舒適度，進而影響使用者的空間感知能力。

---

## **未來研究方向**

未來在沉浸式技術中探索音視覺空間感知的幾個關鍵方向包括：

1. **個人化跨模態整合模型**：目前的方法多基於普遍原則，但研究顯示，個體對於音視覺空間信息的整合存在顯著差異[3]。發展能夠適應個體感知特徵的校準方法，將有助於提升沉浸式技術的體驗品質。
    
2. **跨模態可塑性與新型交互模式**：基於研究表明人類能夠適應新的感官映射關係[4]，未來的系統或可引入非自然的音視覺對應方式，以優化特定任務或彌補現有顯示技術的不足。這將為沉浸式體驗的設計提供新的可能性。
    
3. **基於 AI 的空間音頻計算技術**：機器學習技術在生成個人化 HRTF 模型方面已顯示出潛力[9]，未來還可能應用於即時聲學建模，以更準確地模擬環境中的音效反射、折射與混響。
    
4. **擴展視場的 AR 顯示技術**：目前 AR 顯示的視場限制了音視覺的整合體驗[12]。隨著顯示技術的進步，研究需進一步探討擴展視場後的跨模態整合方式，確保沉浸感的提升。
    
5. **長期適應性研究**：雖然已有研究證明短期內人類可適應新的音視覺映射方式[4]，但長期暴露於沉浸式環境如何影響感知機制仍未有充分研究。理解這些長期適應效應，將對未來技術發展及使用者健康產生深遠影響。
    

未來，隨著技術的不斷發展，深入研究音視覺空間感知將進一步推動沉浸式技術的應用與體驗優化。