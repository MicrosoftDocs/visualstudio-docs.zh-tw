---
title: 步驟 7：新增乘法及除法問題
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 834d7c5825759298ab083ec0d0a0553e87e6173e
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118614"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>步驟 7：新增乘法及除法問題

在本教學課程的第七個部分中，您將加入乘法和除法問題，不過要先思考如何進行這項變更。 思考初始步驟，其中牽涉到儲存值。

> [!NOTE]
> 這個主題是有關基本程式碼撰寫概念的教學課程系列的一部分。
> - 如需教學課程的概觀，請參閱[教學課程 2：建立計時的數學測驗](../ide/tutorial-2-create-a-timed-math-quiz.md)。
> - 若要下載已完成的程式碼版本，請參閱[完整的數學測驗教學課程範例](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)。

## <a name="to-add-multiplication-and-division-problems"></a>若要加入乘法和除法問題

1. 在表單中加入另外四個整數變數。

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     > [!IMPORTANT]
     > 使用此頁面右上方的程式設計語言控制項，以查看C#程式碼片段或 Visual Basic 程式碼片段。<br><br>![Docs.Microsoft.com 的程式設計語言控制項](../ide/media/docs-programming-language-control.png)

2. 如同您先前執行的方式，修改 `StartTheQuiz()` 方法填入乘法和除法問題的隨機數字。

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. 修改 `CheckTheAnswer()` 方法，讓它一併檢查乘法和除法問題。

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     由於使用鍵盤不容易輸入乘號 (×) 和除號 (÷)，因此 Visual C# 和 Visual Basic 可接受星號 (*) 表示乘法和斜線符號 (/) 表示除法。

4. 變更計時器的 <xref:System.Windows.Forms.Timer.Tick> 事件處理常式的最後一部分，讓事件處理常式在時間結束時填入正確答案。

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. 儲存並執行您的程式。

     受測者必須回答四個問題才能完成測驗，如下圖所示。

     ![包含四個問題的數學測驗](../ide/media/express_finishedquiz.png)<br/>
***數學測驗****有四個問題*

## <a name="to-continue-or-review"></a>若要繼續或檢視

- 若要移至下一個教學課程步驟 **，請參閱[步驟8：自訂測驗](../ide/step-8-customize-the-quiz.md)。**

- 若要回到上一個教學課程步驟，請參閱[步驟 6：新增減法問題](../ide/step-6-add-a-subtraction-problem.md)。
