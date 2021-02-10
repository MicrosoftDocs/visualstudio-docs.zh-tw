---
title: 步驟 4：新增 CheckTheAnswer() 方法
description: '瞭解如何撰寫 CheckTheAnswer ( # B1 方法來判斷數學問題的答案是否正確。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f6e52d415b4278a04e559c64cdcfac86cdf22261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950701"
---
# <a name="step-4-add-the-checktheanswer-method"></a>步驟 4：新增 CheckTheAnswer() 方法

在本教學課程的第四個部分中，您將撰寫 `CheckTheAnswer()` 這個方法，用於判斷數學問題的答案是否正確。 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

> [!NOTE]
> 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

## <a name="to-verify-whether-the-answers-are-correct"></a>若要驗證答案是否正確

> [!NOTE]
> 如果您是在 Visual Basic 中依照步驟一路做下來，您將使用 `Function` 關鍵字，而不會使用慣用的 `Sub` 關鍵字，因為這個方法會傳回值。 理由就是這麼簡單：Sub 不會傳回值，但 Function 會傳回值。

1. 新增 `CheckTheAnswer()` 方法。 此方法應該與您所做的其他方法（例如）對齊 `StartTheQuiz()` 。

     呼叫這個方法時，它會將 addend1 和 addend2 的值相加，並且將結果與 sum (總和) <xref:System.Windows.Forms.NumericUpDown> 控制項的值比較。 如果值相等，則方法會傳回 `true` 值。 否則，方法會傳回 `false` 值。 您的程式碼應該看起來與下列範例相同。

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     接下來，您將透過更新方法中的程式碼，讓計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件處理常式呼叫新的 `CheckTheAnswer()` 方法，藉此檢查答案。

2. 將下列程式碼加入至 `if else` 方法中的語句 `Timer1_Tick()` ，讓計時器在使用者取得解答許可權時停止。

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     如果答案正確，`CheckTheAnswer()` 會傳回 `true`。 事件處理常式會停止計時器，並顯示恭喜訊息，然後再次啟用 [開始] 按鈕。 否則，測驗會繼續。

3. 儲存您的程式，執行程式，開始進行測驗，並提供正確答案給加法問題。

    > [!NOTE]
    > 當您輸入答案時，必須在開始輸入答案之前先選取預設值，或是手動刪除零。 您將在本教學課程稍後更正這種行為。

     當您提供正確答案時，訊息方塊隨即開啟，[開始] 按鈕會變成可用，且計時器會停止。

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟，請參閱 **[步驟5：加入 NumericUpDown 控制項的 Enter 事件處理常式](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**。

- 若要回到上一個教學課程步驟，請參閱 [步驟3：加入倒數計時器](../ide/step-3-add-a-countdown-timer.md)。
