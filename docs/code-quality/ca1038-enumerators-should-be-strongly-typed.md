---
title: CA1038：列舉程式應該是強類型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b15295b0af35c927e56c37f56a48c86ac4c705af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898846"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038：列舉程式應該是強類型
|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的型別會實作<xref:System.Collections.IEnumerator?displayProperty=fullName>，但不是提供強類型的版本<xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>屬性。 衍生自下列類型的型別免套用此規則：

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 這項規則要求<xref:System.Collections.IEnumerator>實作同時也提供強類型的版本<xref:System.Collections.IEnumerator.Current%2A>屬性，如此使用者就不需要使用介面所提供的功能時，轉型為強類型傳回的值。 這項規則假設的實作類型<xref:System.Collections.IEnumerator>包含比強型別的執行個體的集合<xref:System.Object>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作介面屬性明確 (將它宣告為`IEnumerator.Current`)。 新增公用的強類型的版本的屬性，宣告為`Current`，並讓它傳回強類型的物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您實作使用，以物件為基礎的集合，例如二進位樹狀目錄的物件為基礎列舉值，則隱藏此規則的警告。 擴充新集合的型別會定義強類型列舉值，並公開強類型的屬性。

## <a name="example"></a>範例
 下列範例會示範正確的方式來實作的強型別<xref:System.Collections.IEnumerator>型別。

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.DictionaryBase?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>