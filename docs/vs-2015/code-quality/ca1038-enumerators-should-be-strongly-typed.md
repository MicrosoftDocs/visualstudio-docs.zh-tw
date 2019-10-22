---
title: CA1038：枚舉器應該是強型別 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661758"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038：列舉程式應該是強類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型會執行 <xref:System.Collections.IEnumerator?displayProperty=fullName>，但不會提供 <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> 屬性的強型別版本。 衍生自下列類型的類型不受此規則所規範：

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 此規則需要 <xref:System.Collections.IEnumerator> 的執行方式也提供 <xref:System.Collections.IEnumerator.Current%2A> 屬性的強型別版本，讓使用者在使用介面所提供的功能時，不需要將傳回值轉換成強式類型。 此規則假設實 <xref:System.Collections.IEnumerator> 的類型包含強于 <xref:System.Object> 之類型實例的集合。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請明確地執行介面屬性（將它宣告為 `IEnumerator.Current`）。 新增屬性的公用強型別版本，並將其宣告為 `Current`，並讓它傳回強型別物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您執行物件型列舉值以搭配以物件為基礎的集合（例如二進位樹狀結構）使用時，請隱藏此規則的警告。 擴充新集合的類型將會定義強型別列舉值，並公開強型別屬性。

## <a name="example"></a>範例
 下列範例示範執行強型別 <xref:System.Collections.IEnumerator> 型別的正確方式。

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>請參閱
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
