---
title: CA1010:集合應該實作泛型介面
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
ms.openlocfilehash: a62120babe98ead6d78b568bc630f46a386edf02
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842654"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010:集合應該實作泛型介面

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|分類|Microsoft.Design|
|中斷變更|非重大|

## <a name="cause"></a>原因

類型會實作<xref:System.Collections.IEnumerable?displayProperty=fullName>介面，但不會實作<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>介面，而且包含的組件的目標.NET。 此規則會忽略實作的型別<xref:System.Collections.IDictionary?displayProperty=fullName>。

根據預設，此規則只會查看外部可見的類型，但這[可設定](#configurability)。

## <a name="rule-description"></a>規則描述

若要放寬集合的可用性，請實作其中一個泛型集合介面。 之後可以使用集合填入泛型集合類型，如下所示：

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請實作其中一個下列的泛型集合介面：

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

安全地隱藏的警告，這項規則;不過，使用集合將會更多限制。

## <a name="configurability"></a>設定功能

如果您執行這項規則，從[FxCop 分析器](install-fxcop-analyzers.md)（而不是透過靜態程式碼分析），您可以設定的哪些部分您程式碼基底上執行這項規則，根據其存取範圍。 比方說，若要指定執行規則時，應該只針對非公用 API 介面，將下列索引鍵 / 值組新增至專案中的.editorconfig 檔案：

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

此類別 （設計） 中，您可以設定此選項，只是這項規則，所有規則，或所有的規則。 如需詳細資訊，請參閱 <<c0> [ 設定的 FxCop 分析器](configure-fxcop-analyzers.md)。

## <a name="example-violation"></a>範例違規

下列範例示範衍生自非泛型類別 （參考型別）`CollectionBase`違反此規則的類別。

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

若要修正此規則的違規情形，請執行下列其中一項：

- 實作泛型介面。
- 變更的基底類別的型別，已實作這兩個泛型和非泛型介面，例如`Collection<T>`類別。

## <a name="fix-by-base-class-change"></a>修正基底類別變更

下列範例會藉由變更集合的基底類別的非泛型修正違規`CollectionBase`泛型類別`Collection<T>`(`Collection(Of T)` Visual Basic 中) 類別。

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

變更已發行的類別的基底類別會被視為現有消費者的中斷變更。

## <a name="fix-by-interface-implementation"></a>介面實作來修正

下列範例會藉由實作這些泛型介面修正違規： `IEnumerable<T>`， `ICollection<T>`，並`IList<T>`(`IEnumerable(Of T)`， `ICollection(Of T)`，和`IList(Of T)`Visual Basic 中)。

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>相關的規則

- [CA1005:避免在泛型類型上的過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000:不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002:不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006:無法建立巢狀成員簽章中的泛型型別](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004:泛型方法應該提供型別參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003： 必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007:在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱

- [泛型](/dotnet/csharp/programming-guide/generics/index)