---
title: CA1010：集合應該實作泛型介面
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3e50fb93e8cdfe6f65fe1b2de1da54b58a6a8c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449318"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010：集合應該實作泛型介面

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|分類|Microsoft. Design|
|重大變更|不中斷|

## <a name="cause"></a>原因

型別會實作用 @no__t 0 介面，但不會執行 @no__t 1 介面，而包含的元件則是以 .NET 為目標。 此規則會忽略實 <xref:System.Collections.IDictionary?displayProperty=fullName> 的類型。

根據預設，此規則只會查看外部可見的類型，但這是[可](#configurability)設定的。

## <a name="rule-description"></a>規則描述

若要放寬集合的可用性，請實作其中一個泛型集合介面。 然後，可以使用集合來填入泛型集合類型，如下所示：

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規，請執行下列其中一個泛型集合介面：

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以放心地隱藏此規則的警告;不過，使用集合會有更多限制。

## <a name="configurability"></a>可設定性

如果您是從[FxCop 分析器](install-fxcop-analyzers.md)執行此規則（而不是使用舊版分析），您可以根據其存取範圍，設定程式碼基底中的哪些部分來執行此規則。 例如，若要指定規則只針對非公用 API 介面執行，請將下列機碼值組新增至專案中的 editorconfig 檔案：

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

您可以只針對此規則、所有規則或此類別中的所有規則（設計）設定此選項。 如需詳細資訊，請參閱[設定 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-violation"></a>範例違規

下列範例顯示的類別（參考型別）衍生自非泛型的 `CollectionBase` 類別，這違反了這項規則。

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

若要修正此規則的違規情形，請執行下列其中一項動作：

- 執行泛型介面。
- 將基類變更為已同時執行泛型和非泛型介面的類型，例如 `Collection<T>` 類別。

## <a name="fix-by-base-class-change"></a>依基類變更修正

下列範例會將集合的基類從非泛型的 `CollectionBase` 類別變更為泛型 `Collection<T>` （Visual Basic）類別中的 `Collection(Of T)`，藉以修正違規。

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

變更已發行類別的基類，會被視為對現有取用者的重大變更。

## <a name="fix-by-interface-implementation"></a>依介面執行修正

下列範例會藉由執行下列泛型介面來修正違規： `IEnumerable<T>`、`ICollection<T>` 和 `IList<T>` （`IEnumerable(Of T)`、`ICollection(Of T)`，以及 @no__t 中的 Visual Basic-5）。

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>相關規則

- [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)
