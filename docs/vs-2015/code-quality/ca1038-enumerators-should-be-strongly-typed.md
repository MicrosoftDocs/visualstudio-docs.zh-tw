---
title: CA1038： 列舉程式應該強型別 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aafd89a068a57ef1eb89584441195e1ece8b8f52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899067"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038：列舉程式應該是強類型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的型別會實作<xref:System.Collections.IEnumerator?displayProperty=fullName>但不提供強型別的版本<xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>屬性。 衍生自下列類型的類型為免套用此規則：

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則描述
 這項規則要求<xref:System.Collections.IEnumerator>實作也提供強型別的版本<xref:System.Collections.IEnumerator.Current%2A>屬性，因此使用者不需要傳回值轉換成強型別時使用介面所提供的功能。 這項規則假設，實作型別<xref:System.Collections.IEnumerator>包含比強型別的執行個體的集合<xref:System.Object>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，實作介面屬性明確 (將它宣告為`IEnumerator.Current`)。 新增屬性，宣告為公用強型別的版本`Current`，並且會傳回強類型的物件。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您實作用於物件為基礎的集合，例如二進位樹狀目錄的物件為基礎的列舉值，則隱藏此規則的警告。 擴充新集合的型別會定義強型別列舉值，並公開 （expose） 的強型別的屬性。

## <a name="example"></a>範例
 下列範例會示範正確的方式來實作強型別<xref:System.Collections.IEnumerator>型別。

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>相關的規則
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



