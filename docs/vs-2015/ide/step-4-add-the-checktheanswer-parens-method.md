---
title: 步驟 4：新增 CheckTheAnswer() 方法 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbfdc15b06d857b7537a4a327f3201c86d4db2d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671772"
---
# <a name="step-4-add-the-checktheanswer-method"></a>步驟 4：加入 CheckTheAnswer() 方法
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本教學課程的第四個部分中，您將撰寫 `CheckTheAnswer()` 這個方法，用於判斷數學問題的答案是否正確。 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

> [!NOTE]
> 如果您是在 Visual Basic 中依照步驟一路做下來，您將使用 `Function` 關鍵字，而不會使用慣用的 `Sub` 關鍵字，因為這個方法會傳回值。 理由就是這麼簡單：Sub 不會傳回值，但 Function 會傳回值。

### <a name="to-verify-whether-the-answers-are-correct"></a>若要驗證答案是否正確

1. 加入 `CheckTheAnswer()` 方法。

     呼叫這個方法時，它會將 addend1 和 addend2 的值相加，並且將結果與 sum (總和) `NumericUpDown` 控制項的值比較。 如果值相等，則方法會傳回 `true` 值。 否則，方法會傳回 `false` 值。 您的程式碼應該看起來與下列範例相同。

     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]

     接下來，您將透過更新方法中的程式碼，讓計時器的 Tick 事件處理常式呼叫新的 `CheckTheAnswer()` 方法，藉此檢查答案。

2. 將下列程式碼加入至 `if else` 陳述式。

     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]

     如果答案正確，`CheckTheAnswer()` 會傳回 `true`。 事件處理常式會停止計時器，並顯示恭喜訊息，然後再次啟用 [開始] 按鈕。 否則，測驗會繼續。

3. 儲存您的程式，執行程式，開始進行測驗，並提供正確答案給加法問題。

    > [!NOTE]
    > 當您輸入答案時，必須在開始輸入答案之前先選取預設值，或是手動刪除零。 您將在本教學課程稍後更正這種行為。

     當您提供正確答案時，訊息方塊隨即開啟，[開始] 按鈕會變成可用，且計時器會停止。

### <a name="to-continue-or-review"></a>繼續或檢視

- 若要移到下一個教學課程步驟，請參閱[步驟 5：新增 NumericUpDown 控制項的 Enter 事件處理常式](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)。

- 若要回到上一個教學課程步驟，請參閱[步驟 3：新增倒數計時器](../ide/step-3-add-a-countdown-timer.md)。
