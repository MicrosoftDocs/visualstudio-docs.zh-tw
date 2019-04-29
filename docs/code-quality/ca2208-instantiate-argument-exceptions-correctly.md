---
title: CA2208:必須正確執行個體化引數例外狀況
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d82b1884336b314e8fcede3c6041030a878b999c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806760"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208:必須正確執行個體化引數例外狀況

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|分類|Microsoft.Usage|
|中斷變更|非中斷|

## <a name="cause"></a>原因

可能的原因包括下列情況：

- 例外狀況類型，或衍生自預設 （無參數） 建構函式進行呼叫<xref:System.ArgumentException>。

- 不正確的字串引數傳遞至參數化建構函式，或衍生自例外狀況類型<xref:System.ArgumentException>。

## <a name="rule-description"></a>規則描述

而不是呼叫預設建構函式，呼叫其中一個建構函式多載，可讓提供更有意義的例外狀況訊息。 例外狀況訊息應該為目標的開發人員，並清楚地說明錯誤狀況，以及如何修正或避免此例外狀況。

一個和兩個字串的建構函式的簽章<xref:System.ArgumentException>和其衍生的類型不一致，相對於`message`和`paramName`參數。 請確定正確的字串引數來呼叫這些建構函式。 簽章如下所示：

 <xref:System.ArgumentException>(字串`message`)

 <xref:System.ArgumentException>(字串`message`，字串`paramName`)

 <xref:System.ArgumentNullException>(字串`paramName`)

 <xref:System.ArgumentNullException>(字串`paramName`，字串`message`)

 <xref:System.ArgumentOutOfRangeException>(字串`paramName`)

 <xref:System.ArgumentOutOfRangeException>(字串`paramName`，字串`message`)

 <xref:System.DuplicateWaitObjectException>(字串`parameterName`)

 <xref:System.DuplicateWaitObjectException>(字串`parameterName`，字串`message`)

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，呼叫的建構函式的訊息、 參數名稱，或兩者，並請確定引數類型的適當<xref:System.ArgumentException>所呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 它是安全地隱藏此規則的警告，只有當參數化建構函式以正確的字串引數呼叫。

## <a name="example-1"></a>範例 1
 下列範例顯示不正確地具現化 ArgumentNullException 型別的執行個體的建構函式。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

## <a name="example-2"></a>範例 2
 下列範例會修正上述的違規情形，藉由切換的建構函式引數。

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]