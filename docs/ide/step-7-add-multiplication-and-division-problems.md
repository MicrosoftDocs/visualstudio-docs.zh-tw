---
title: "步驟 7：新增乘法和除法問題 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 481d1ad8050a0b028a7cbf23f9385c9920feb1a2
ms.contentlocale: zh-tw
ms.lasthandoff: 09/06/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>步驟 7：加入乘法和除法問題
在本教學課程的第七個部分中，您將加入乘法和除法問題，不過要先思考如何進行這項變更。 思考初始步驟，其中牽涉到儲存值。  
  
### <a name="to-add-multiplication-and-division-problems"></a>若要加入乘法和除法問題  
  
1.  在表單中加入另外四個整數變數。  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  如同您先前執行的方式，修改 `StartTheQuiz()` 方法填入乘法和除法問題的隨機數字。  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  修改 `CheckTheAnswer()` 方法，讓它一併檢查乘法和除法問題。  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     由於使用鍵盤不容易輸入乘號 (×) 和除號 (÷)，因此 Visual C# 和 Visual Basic 可接受星號 (*) 表示乘法和斜線符號 (/) 表示除法。  
  
4.  變更計時器的 Tick 事件處理常式的最後一部分，讓事件處理常式在時間結束時填入正確答案。  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  儲存並執行您的程式。  
  
     受測者必須回答四個問題才能完成測驗，如下圖所示。  
  
     ![包含四個問題的數學測驗](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
包含四個問題的數學測驗  
  
### <a name="to-continue-or-review"></a>繼續或檢視  
  
-   若要移到下一個教學課程步驟，請參閱[步驟 8：自訂測驗](../ide/step-8-customize-the-quiz.md)。  
  
-   若要回到上一個教學課程步驟，請參閱[步驟 6：新增減法問題](../ide/step-6-add-a-subtraction-problem.md)。
