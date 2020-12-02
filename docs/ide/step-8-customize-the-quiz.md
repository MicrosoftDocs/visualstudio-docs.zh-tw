---
title: 步驟 8：自訂測驗
description: 瞭解如何將 timeLabel 控制項轉換成不同的色彩，並為測驗人員提供提示。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21403aeb51f342f607575d99a79ce2bdb7aaa54a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479312"
---
# <a name="step-8-customize-the-quiz"></a>步驟 8：自訂測驗

在本教學課程的最後一部分，您將探索一些方法來自訂測驗，以及延伸您已經學習過的內容。 例如，請了解程式如何建立答案絕不是分數的隨機除法問題。 若要深入了解，請將 `timeLabel` 控制項轉換為不同的色彩，並提供受測者的提示。

> [!NOTE]
> 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

## <a name="to-customize-the-quiz"></a>自訂測驗

- 當測驗中只剩下五秒時，請設定其 **背景** 色彩屬性以將 **timeLabel** 控制項變成紅色。

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  在測驗結束時重設色彩。

- 在 <xref:System.Windows.Forms.NumericUpDown> 控制項中輸入正確答案時，透過播放音效來提供受測者的提示。 (您必須撰寫每個控制項之 <xref:System.Windows.Forms.NumericUpDown.ValueChanged> 事件的事件處理常式，而只要受測者變更控制項的值時就會引發該事件)。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程，請參閱 **[教學課程3：建立配對遊戲](../ide/tutorial-3-create-a-matching-game.md)**。

- 若要回到上一個教學課程步驟，請參閱 [步驟7：新增乘法和除法問題](../ide/step-7-add-multiplication-and-division-problems.md)。
