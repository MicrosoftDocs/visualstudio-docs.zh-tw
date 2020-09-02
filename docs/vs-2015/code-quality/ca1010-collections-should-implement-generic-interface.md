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
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545518"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010:集合應該實作泛型介面
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|類別|Microsoft. 設計|
|中斷變更|非中斷|

## <a name="cause"></a>原因
 外部可見的類型 <xref:System.Collections.IEnumerable?displayProperty=fullName> 會執行介面，但不會執行 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 介面和包含元件目標 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 。 此規則會忽略執行的類型 <xref:System.Collections.IDictionary?displayProperty=fullName> 。

## <a name="rule-description"></a>規則描述
 若要放寬集合的可用性，請實作其中一個泛型集合介面。 然後，集合可以用來填入泛型集合類型，如下所示：

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請執行下列其中一個泛型集合介面：

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 隱藏此規則的警告是安全的;不過，此集合將會有更多的使用限制。

## <a name="example-violation"></a>違規範例

### <a name="description"></a>描述
 下列範例示範衍生自非泛型類別的類別 (參考) 型別 `CollectionBase` ，而此類別違反了這項規則。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>註解
 若要修正違反此違規的情況，您應該執行泛型介面，或將基類變更為已經同時實作為泛型和非泛型介面（例如類別）的型別 `Collection<T>` 。

## <a name="fix-by-base-class-change"></a>依基類變更進行修正

### <a name="description"></a>描述
 下列範例會藉由將集合的基類從非泛型 `CollectionBase` 類別變更為 `Collection<T>` `Collection(Of T)`) 類別中的泛型 (，以修正違規 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>註解
 變更已發行之類別的基類，會視為對現有取用者的重大變更。

## <a name="fix-by-interface-implementation"></a>依介面實行修正

### <a name="description"></a>描述
 下列範例會藉由執行下列泛型介面來修正違規： `IEnumerable<T>` 、 `ICollection<T>` 和 `IList<T>` (`IEnumerable(Of T)` 、 `ICollection(Of T)` 和 `IList(Of T)` 在) 中 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 。

### <a name="code"></a>程式碼
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002：不要公開泛型清單](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007:建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
