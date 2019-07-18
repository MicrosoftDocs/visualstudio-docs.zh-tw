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
ms.openlocfilehash: 2110a8d0b58d87a4554971cf00af6441d293aa91
ms.sourcegitcommit: 92a04c57ac0a49f304fa2ea5043436f30068c3cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975882"
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

- 呼叫預設 （無參數） 建構函式的例外狀況型別，或衍生自， <xref:System.ArgumentException>。

- 不正確的字串引數傳遞至參數化建構函式的例外狀況型別，或衍生自， <xref:System.ArgumentException>。

## <a name="rule-description"></a>規則描述

而不是呼叫預設建構函式，呼叫其中一個建構函式多載，可讓提供更有意義的例外狀況訊息。 例外狀況訊息應該為目標的開發人員，並清楚地說明錯誤狀況，以及如何修正或避免此例外狀況。

一個和兩個字串的建構函式的簽章<xref:System.ArgumentException>和其衍生的類型不一致的位置`message`和`paramName`參數。 請確定正確的字串引數來呼叫這些建構函式。 簽章如下所示：

- <xref:System.ArgumentException>(字串`message`)
- <xref:System.ArgumentException>(字串`message`，字串`paramName`)
- <xref:System.ArgumentNullException>(字串`paramName`)
- <xref:System.ArgumentNullException>(字串`paramName`，字串`message`)
- <xref:System.ArgumentOutOfRangeException>(字串`paramName`)
- <xref:System.ArgumentOutOfRangeException>(字串`paramName`，字串`message`)
- <xref:System.DuplicateWaitObjectException>(字串`parameterName`)
- <xref:System.DuplicateWaitObjectException>(字串`parameterName`，字串`message`)

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，呼叫的建構函式的訊息、 參數名稱，或兩者，並請確定引數類型的適當<xref:System.ArgumentException>所呼叫。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

它是安全地隱藏此規則的警告，只有當參數化建構函式以正確的字串引數呼叫。

## <a name="example"></a>範例

下列程式碼會顯示不正確地具現化的執行個體的建構函式<xref:System.ArgumentNullException>。

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]

下列程式碼修正上述違規，藉由切換的建構函式引數。

[!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs?range=3-6)]
[!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]

## <a name="related-rules"></a>相關的規則

- [CA1507:使用 nameof 取代字串](ca1507.md)