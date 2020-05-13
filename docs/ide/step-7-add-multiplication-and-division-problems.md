---
title: 步驟 7：加入乘法和除法問題
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579786"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>步驟 7：加入乘法和除法問題

在本教學課程的第七個部分中，您將加入乘法和除法問題，不過要先思考如何進行這項變更。 思考初始步驟，其中牽涉到儲存值。

> [!NOTE]
> 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。

## <a name="to-add-multiplication-and-division-problems"></a>若要加入乘法和除法問題

1. 在表單中加入另外四個整數變數。

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. 如同您先前執行的方式，修改 `StartTheQuiz()` 方法填入乘法和除法問題的隨機數字。

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. 修改 `CheckTheAnswer()` 方法，讓它一併檢查乘法和除法問題。

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     不能使用鍵盤輕鬆輸入乘法符號 （*） 和除法符號 （*），因此 C# 和 Visual Basic 接受乘法用星號 （*） 和除法斜線標記 （/）。

4. 變更計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件處理常式的最後一部分，讓事件處理常式在時間結束時填入正確答案。

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. 儲存並執行您的程式。

     受測者必須回答四個問題才能完成測驗，如下圖所示。

     ![包含四個問題的數學測驗](../ide/media/express_finishedquiz.png)<br/>
***數學測驗****有四個問題*

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 要轉到下一個教程步驟，請參閱**[步驟 8：自訂測驗](../ide/step-8-customize-the-quiz.md)**。

- 若要回到上一個教學課程步驟，請參閱[步驟 6：新增減法問題](../ide/step-6-add-a-subtraction-problem.md)。
