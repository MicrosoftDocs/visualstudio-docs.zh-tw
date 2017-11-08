---
title: "步驟 8：自訂測驗 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# 步驟 8：自訂測驗
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

本教學課程中的最後一部分，您將會探索某些方式來自訂測驗以及拓展您已經學會的部分。  例如，假設程式如何建立答案不會是一個分數的隨機除法問題。  若要進一步了解，請將 `timeLabel` 控制項變成不同色彩並將提示給測試者。  
  
### 若要自訂測驗  
  
-   當只有五秒測試時，藉由設定它的 **背景色彩** 屬性，請將**timeLabel**控制項轉為紅色 \(`timeLabel.BackColor = Color.Red;`\)。  當測驗結束時，重設色彩。  
  
-   當測試者在其中一個 NumericUpDown 控制項中輸入正確答案時，播放音效來提示測試者 \(您必須為每一個控制項的`ValueChanged()`事件撰寫事件處理常式，每當測試者變更控制項的值時，就會引發此事件\)。  
  
### 若要繼續或檢視  
  
-   若要下載測驗的完整版，請參閱[完整的數學測驗教學課程範例](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) \(英文\)。  
  
-   若要移到下一個教學課程，請參閱[教學課程 3：建立配對遊戲](../ide/tutorial-3-create-a-matching-game.md)。  
  
-   若要回到上一個教學課程步驟，請參閱[步驟 7：加入乘法和除法問題](../ide/step-7-add-multiplication-and-division-problems.md)。