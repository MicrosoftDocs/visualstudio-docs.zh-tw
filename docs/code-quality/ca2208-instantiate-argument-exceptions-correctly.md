---
title: "CA2208： 正確執行個體化引數例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4cb25017750ee95d55f1c776dea1f062f24ec22c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208：請正確執行個體化引數例外狀況
|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|分類|Microsoft.Usage|  
|中斷變更|非中斷|  
  
## <a name="cause"></a>原因  
 可能的原因包括下列情況：  
  
-   例外狀況類型，或衍生自預設 （無參數） 建構函式進行呼叫<xref:System.ArgumentException>。  
  
-   不正確的字串引數傳遞至參數化建構函式的例外狀況類型，或衍生自<xref:System.ArgumentException>。  
  
## <a name="rule-description"></a>規則描述  
 而不是呼叫預設建構函式，呼叫其中一個建構函式多載，可讓提供更有意義的例外狀況訊息。 例外狀況訊息應該以開發人員為目標，並清楚地說明錯誤狀況，以及如何修正或避免此例外狀況。  
  
 一個和兩個字串的建構函式的簽章<xref:System.ArgumentException>和其衍生的類型不一致，相對於`message`和`paramName`參數。 請確定以正確的字串引數來呼叫這些建構函式。 簽章如下所示：  
  
 <xref:System.ArgumentException>(字串`message`)  
  
 <xref:System.ArgumentException>(字串`message`，字串`paramName`)  
  
 <xref:System.ArgumentNullException>(字串`paramName`)  
  
 <xref:System.ArgumentNullException>(字串`paramName`，字串`message`)  
  
 <xref:System.ArgumentOutOfRangeException>(字串`paramName`)  
  
 <xref:System.ArgumentOutOfRangeException>(字串`paramName`，字串`message`)  
  
 <xref:System.DuplicateWaitObjectException>(字串`parameterName`)  
  
 <xref:System.DuplicateWaitObjectException>(字串`parameterName`，字串`message`)  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，呼叫的建構函式會採用訊息、 參數名稱，或兩者，並請確定引數類型的適當<xref:System.ArgumentException>所呼叫。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 它可以安全地隱藏此規則的警告，只有當參數化建構函式呼叫正確的字串引數。  
  
## <a name="example"></a>範例  
 下列範例顯示不正確地具現化 ArgumentNullException 類型的執行個體的建構函式。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例會修正上述的違規，藉由切換的建構函式引數。  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]