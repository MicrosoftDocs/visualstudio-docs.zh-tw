---
title: CA1005：避免在泛型型別上有過多的參數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7e75b2e295a561e026b437b3c62724536a3ac64e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671979"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005：避免在泛型類型上包含過多參數
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的泛型型別有兩個以上的型別參數。

## <a name="rule-description"></a>規則描述
 泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 通常會有一個型別參數（如 `List<T>`），而且在有兩個型別參數的某些情況下很明顯，如 `Dictionary<TKey, TValue>` 中所示。 如果有兩個以上的型別參數存在，大部分使用者的困難程度就會變得太大C# （例如，`TooManyTypeParameters<T, K, V>` 或 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 中的 `TooManyTypeParameters(Of T, K, V)`）。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將設計變更為不使用兩個以上的類型參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非設計絕對需要兩個以上的類型參數，否則請勿隱藏此規則的警告。 以易於瞭解和使用的語法提供泛型，可減少學習及增加新程式庫採用率所需的時間。

## <a name="related-rules"></a>相關規則
 [CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
