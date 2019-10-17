---
title: CA1005：避免在泛型類型上包含過多參數
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77f913a2dc31ee77445ee90b417f1a7d1cf23b8d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449355"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005：避免在泛型類型上包含過多參數

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|分類|Microsoft. Design|
|重大變更|中斷|

## <a name="cause"></a>原因
外部可見的泛型型別有兩個以上的型別參數。

## <a name="rule-description"></a>規則描述
泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 通常會有一個型別參數（如 `List<T>`），而且在有兩個型別參數的某些情況下很明顯，如 `Dictionary<TKey, TValue>` 中所示。 如果有兩個以上的型別參數存在，大部分使用者的困難程度就會變得太大（例如C# ，在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中，或 `TooManyTypeParameters(Of T, K, V)` 中的 `TooManyTypeParameters<T, K, V>`）。

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
[泛型](/dotnet/csharp/programming-guide/generics/index)
