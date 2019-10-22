---
title: CA1010：集合應該執行泛型介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 20238a844b45221207ca952d90d172ac720136ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655257"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010：集合應該實作泛型介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Category|Microsoft. Design|
|中斷變更|不中斷|

## <a name="cause"></a>原因
 外部可見的類型會實 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面，但不會執行 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面，而包含的元件會以 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 為目標。 此規則會忽略實 <xref:System.Collections.IDictionary?displayProperty=fullName> 的類型。

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
 您可以放心地隱藏此規則的警告;不過，集合會有更多的使用限制。

## <a name="example-violation"></a>範例違規

### <a name="description"></a>描述
 下列範例顯示的類別（參考型別）衍生自非泛型的 `CollectionBase` 類別，這違反了這項規則。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>註解
 若要修正違反此違規的情形，您應該執行泛型介面，或將基類變更為已經實作為泛型和非泛型介面的型別，例如 `Collection<T>` 類別。

## <a name="fix-by-base-class-change"></a>依基類變更修正

### <a name="description"></a>描述
 下列範例會藉由將集合的基類從非泛型 `CollectionBase` 類別變更為泛型 `Collection<T>` （`Collection(Of T)` 在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]）類別中，來修正違規。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>註解
 變更已發行類別的基類，會被視為對現有取用者的重大變更。

## <a name="fix-by-interface-implementation"></a>依介面執行修正

### <a name="description"></a>描述
 下列範例會藉由執行下列泛型介面來修正違規： `IEnumerable<T>`、`ICollection<T>` 和 `IList<T>` （`ICollection(Of T)` 中的 `IEnumerable(Of T)`、`IList(Of T)` 和 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]）。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型型別上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000：不要在泛型型別上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：必須使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
