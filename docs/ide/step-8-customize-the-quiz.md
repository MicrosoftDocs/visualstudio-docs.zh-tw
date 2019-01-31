---
title: 步驟 8：自訂測驗
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab5e24d046e3b81b507be558f667583fed0ae1e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55022491"
---
# <a name="step-8-customize-the-quiz"></a>步驟 8：自訂測驗
在本教學課程的最後一部分，您將探索一些方法來自訂測驗，以及延伸您已經學習過的內容。 例如，請了解程式如何建立答案絕不是分數的隨機除法問題。 若要深入了解，請將 `timeLabel` 控制項轉換為不同的色彩，並提供受測者的提示。

## <a name="to-customize-the-quiz"></a>自訂測驗

-   測驗只剩五秒時，請將 [timeLabel] 控制項轉換為紅色，方法是設定其 [BackColor] 屬性 (`timeLabel.BackColor = Color.Red;`)。 在測驗結束時重設色彩。

-   在 <xref:System.Windows.Forms.NumericUpDown> 控制項中輸入正確答案時，透過播放音效來提供受測者的提示。 (您必須撰寫每個控制項之 <xref:System.Windows.Forms.NumericUpDown.ValueChanged> 事件的事件處理常式，而只要受測者變更控制項的值時就會引發該事件)。

## <a name="to-continue-or-review"></a>若要繼續或檢視

-   若要下載完整版的測驗，請參閱[完整的數學測驗教學課程範例](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c) \(英文\)。

-   若要前往下一個教學課程，請參閱[教學課程 3：建立配對遊戲](../ide/tutorial-3-create-a-matching-game.md)。

-   若要回到上一個教學課程步驟，請參閱[步驟 7：新增乘法及除法問題](../ide/step-7-add-multiplication-and-division-problems.md)。
