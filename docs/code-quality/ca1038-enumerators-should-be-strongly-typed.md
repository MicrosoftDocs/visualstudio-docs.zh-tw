---
title: CA1038:列舉程式應該是強類型
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56c2281f76b9064427d1d651523b9cda441eb029
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236007"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038:列舉程式應該是強類型

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|分類|Microsoft.Design|
|重大變更|中斷|

## <a name="cause"></a>原因
公用或受保護的類型<xref:System.Collections.IEnumerator?displayProperty=fullName>會執行， <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>但不會提供屬性的強型別版本。 衍生自下列類型的類型不受此規則所規範：

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
此規則要求<xref:System.Collections.IEnumerator>的<xref:System.Collections.IEnumerator.Current%2A>執行也會提供屬性的強型別版本，因此使用者在使用介面所提供的功能時，不需要將傳回值轉換成強式類型。 此規則假設所執行的類型<xref:System.Collections.IEnumerator>包含強于<xref:System.Object>之類型實例的集合。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規，請明確地執行介面屬性（將它`IEnumerator.Current`宣告為）。 加入屬性的公用強型別版本，並將其`Current`宣告為，並讓它傳回強型別物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
當您執行物件型列舉值以搭配以物件為基礎的集合（例如二進位樹狀結構）使用時，請隱藏此規則的警告。 擴充新集合的類型將會定義強型別列舉值，並公開強型別屬性。

## <a name="example"></a>範例
下列範例示範執行強<xref:System.Collections.IEnumerator>型別類型的正確方式。

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1035ICollection 實現具有強型別成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039清單為強型別](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>