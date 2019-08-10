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
ms.openlocfilehash: ffc94a04d708315cc143afd1556cb8a2f0072e91
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923292"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005：避免在泛型類型上包含過多參數

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
外部可見的泛型型別有兩個以上的型別參數。

## <a name="rule-description"></a>規則描述
泛型類型所包含的類型參數越多，就越難了解並記住每個類型參數所代表的含意。 通常會有一個型別參數 (如`List<T>`), 而且在具有兩個型別參數的某些情況下很明顯, 如同中`Dictionary<TKey, TValue>`的。 如果有兩個以上的型別參數, 很難讓大部分的使用者 (例如`TooManyTypeParameters<T, K, V>` , 在C#或`TooManyTypeParameters(Of T, K, V)`中[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) 變得太大。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請將設計變更為不使用兩個以上的類型參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
除非設計絕對需要兩個以上的類型參數, 否則請勿隱藏此規則的警告。 以易於瞭解和使用的語法提供泛型, 可減少學習及增加新程式庫採用率所需的時間。

## <a name="related-rules"></a>相關規則
[CA1010集合應執行泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006不要在成員簽章中嵌套泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 必須使用一般事件處理常式實例](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 建議適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
[泛型](/dotnet/csharp/programming-guide/generics/index)