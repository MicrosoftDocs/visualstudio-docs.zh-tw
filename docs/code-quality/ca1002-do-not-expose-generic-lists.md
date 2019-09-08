---
title: CA1002：不要公開泛型清單
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 621bb7292ca467d6d3197636f662a4662712d483
ms.sourcegitcommit: 0f44ec8ba0263056ad04d2d0dc904ad4206ce8fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70766015"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002：不要公開泛型清單

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

類型包含外部可見成員，其<xref:System.Collections.Generic.List%601?displayProperty=fullName>為類型、 <xref:System.Collections.Generic.List%601>傳回類型， <xref:System.Collections.Generic.List%601>或其簽章包含參數。

## <a name="rule-description"></a>規則描述

<xref:System.Collections.Generic.List%601?displayProperty=fullName>是針對效能和非繼承而設計的泛型集合。 <xref:System.Collections.Generic.List%601>不包含虛擬成員，可讓您更輕鬆地變更繼承類別的行為。 下列泛型集合是針對繼承而設計，應該公開而不<xref:System.Collections.Generic.List%601>是。

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請<xref:System.Collections.Generic.List%601?displayProperty=fullName>將類型變更為針對繼承而設計的其中一個泛型集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

除非引發此警告的元件不是可重複使用的程式庫，否則請勿隱藏此規則的警告。 例如，在效能調整的應用程式中隱藏此警告是很安全的，因為使用了泛型清單的效能優勢。

## <a name="related-rules"></a>相關規則

[CA1005避免在泛型型別上有過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010集合應執行泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006不要在成員簽章中嵌套泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003 必須使用一般事件處理常式實例](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 建議適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱

[泛型](/dotnet/csharp/programming-guide/generics/index)
