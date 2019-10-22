---
title: CA1035： ICollection 實現具有強型別成員 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d112e2dfb704a785db6bbc5becd2b369d90605b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661838"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035：ICollection 實作包含強類型成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型會執行 <xref:System.Collections.ICollection?displayProperty=fullName>，但不會提供 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> 的強型別方法。 @No__t_0 的強型別版本必須接受兩個參數，而且不能有 <xref:System.Array?displayProperty=fullName> 或 <xref:System.Object?displayProperty=fullName> 陣列做為第一個參數。

## <a name="rule-description"></a>規則描述
 此規則需要 <xref:System.Collections.ICollection> 的執行，才能提供強型別成員，讓使用者在使用介面所提供的功能時，不需要將引數轉換成 <xref:System.Object> 類型。 此規則假設實 <xref:System.Collections.ICollection> 的型別會這麼做，以管理比 <xref:System.Object> 更強之型別的實例集合。

 <xref:System.Collections.ICollection> 會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。 如果集合中的物件延伸 <xref:System.ValueType?displayProperty=fullName>，您就必須為 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 提供強型別成員，以避免因裝箱而造成的效能降低。 當集合的物件為參考型別時，這不是必要的。

 若要執行介面成員的強型別版本，請使用 `InterfaceName.InterfaceMemberName` 格式的名稱（例如 <xref:System.Collections.ICollection.CopyTo%2A>）明確地執行介面成員。 明確的介面成員會使用介面所宣告的資料類型。 使用介面成員名稱（例如 <xref:System.Collections.ICollection.CopyTo%2A>）來執行強型別成員。 將強型別成員宣告為 public，並將參數和傳回值宣告為集合所管理的強式類型。 強型別會取代由介面所宣告的較弱類型，例如 <xref:System.Object> 和 <xref:System.Array>。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請明確地執行介面成員（將它宣告為 <xref:System.Collections.ICollection.CopyTo%2A>）。 加入公開的強型別成員，宣告為 `CopyTo`，並讓它接受強型別陣列做為第一個參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您要執行以物件為基礎的新集合（例如二進位樹狀結構），而擴充新集合的類型會決定強型別，請隱藏此規則的警告。 這些類型應符合這項規則，並公開強型別成員。

## <a name="example"></a>範例
 下列範例示範執行 <xref:System.Collections.ICollection> 的正確方式。

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>請參閱
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
