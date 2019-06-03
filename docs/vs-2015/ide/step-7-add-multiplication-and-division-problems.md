---
title: 步驟 7：新增乘法和除法問題 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 47623d7a65de85b50ad1910425052288a261e49d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109578"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>步驟 7：新增乘法及除法問題
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在本教學課程的第七個部分中，您將加入乘法和除法問題，不過要先思考如何進行這項變更。 思考初始步驟，其中牽涉到儲存值。  
  
### <a name="to-add-multiplication-and-division-problems"></a>若要加入乘法和除法問題  
  
1. 在表單中加入另外四個整數變數。  
  
     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]  
  
2. 如同您先前執行的方式，修改 `StartTheQuiz()` 方法填入乘法和除法問題的隨機數字。  
  
     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]  
  
3. 修改 `CheckTheAnswer()` 方法，讓它一併檢查乘法和除法問題。  
  
     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]  
  
     由於使用鍵盤不容易輸入乘號 (×) 和除號 (÷)，因此 Visual C# 和 Visual Basic 可接受星號 (*) 表示乘法和斜線符號 (/) 表示除法。  
  
4. 變更計時器的 Tick 事件處理常式的最後一部分，讓事件處理常式在時間結束時填入正確答案。  
  
     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]  
  
5. 儲存並執行您的程式。  
  
     受測者必須回答四個問題才能完成測驗，如下圖所示。  
  
     ![包含四個問題的數學測驗](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
包含四個問題的數學測驗  
  
### <a name="to-continue-or-review"></a>若要繼續或檢視  
  
- 若要前往下一個教學課程步驟，請參閱[步驟 8：自訂測驗](../ide/step-8-customize-the-quiz.md)。  
  
- 若要回到上一個教學課程步驟，請參閱[步驟 6：加入減法問題](../ide/step-6-add-a-subtraction-problem.md)。
