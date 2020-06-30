---
title: CA1002：不要公開泛型清單 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546844"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002：不要公開泛型清單
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 類型包含外部可見成員，其為 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 類型、傳回 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 類型，或其簽章包含 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 參數。

## <a name="rule-description"></a>規則描述
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>是針對效能和非繼承而設計的泛型集合。 <xref:System.Collections.Generic.List%601?displayProperty=fullName>不包含虛擬成員，可讓您更輕鬆地變更繼承類別的行為。 下列泛型集合是針對繼承而設計，應該公開而不是 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 。

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 類型變更為針對繼承而設計的其中一個泛型集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 除非引發此警告的元件不是可重複使用的程式庫，否則請勿隱藏此規則的警告。 例如，在效能調整的應用程式中隱藏此警告是很安全的，因為使用了泛型清單的效能優勢。

## <a name="related-rules"></a>相關規則
 [CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010:集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006：不要在成員簽章中將泛型類型巢狀化](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003：使用一般事件處理常式執行個體](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007:建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>另請參閱
 [泛型](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
