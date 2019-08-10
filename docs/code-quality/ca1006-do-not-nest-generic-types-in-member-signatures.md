---
title: CA1006：不要在成員簽章中將泛型類型巢狀化
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 20bee606fd8cd98482a7304e068aaa7cbd5773a7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923231"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006：不要在成員簽章中將泛型類型巢狀化

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
外部可見成員的簽章包含一個巢狀型別引數。

## <a name="rule-description"></a>規則描述
巢狀型別引數就是也是泛型類型的型別引數。 若要呼叫其簽章含有巢狀型別引數的成員，則使用者必須具現化 (Instantiate) 一個泛型類型，並將這個類型傳遞給第二個泛型類型的建構函式。 必要程序及語法十分複雜，且應予以避免。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規情形, 請將設計變更為移除 nested 類型引數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
請勿隱藏此規則的警告。 以易於瞭解和使用的語法提供泛型, 可減少學習及增加新程式庫採用率所需的時間。

## <a name="example"></a>範例
下列範例顯示違反規則的方法, 以及呼叫違規方法所需的語法。

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1005避免在泛型型別上有過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010集合應執行泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 必須使用一般事件處理常式實例](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 建議適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
[泛型](/dotnet/csharp/programming-guide/generics/index)