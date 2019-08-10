---
title: CA1035:ICollection 的實作有強類型成員
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922822"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035:ICollection 的實作有強類型成員

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
公用或受保護的類型<xref:System.Collections.ICollection?displayProperty=fullName>會執行, 但不會提供的<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>強型別方法。 強型別版本的<xref:System.Collections.ICollection.CopyTo%2A>必須接受兩個參數, 而且不<xref:System.Array?displayProperty=fullName>能有或陣列<xref:System.Object?displayProperty=fullName>做為它的第一個參數。

## <a name="rule-description"></a>規則描述
這項規則<xref:System.Collections.ICollection>需要提供強型別成員, 讓使用者在使用介面所提供的功能時<xref:System.Object> , 不需要將引數轉換成型別。 此規則假設<xref:System.Collections.ICollection>執行的型別會管理型別實例的集合, 而該類型比<xref:System.Object>更強。

 <xref:System.Collections.ICollection> 會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。 如果集合中的物件擴充<xref:System.ValueType?displayProperty=fullName>, 您必須提供的強型別<xref:System.Collections.IEnumerable.GetEnumerator%2A>成員, 以避免因裝箱而造成的效能降低。 當集合的物件為參考型別時, 這不是必要的。

若要執行介面成員的強型別版本, 請使用表單`InterfaceName.InterfaceMemberName`中的名稱 ( <xref:System.Collections.ICollection.CopyTo%2A>例如) 來明確地執行介面成員。 明確的介面成員會使用介面所宣告的資料類型。 使用介面成員名稱 (例如<xref:System.Collections.ICollection.CopyTo%2A>) 來執行強型別成員。 將強型別成員宣告為 public, 並將參數和傳回值宣告為集合所管理的強式類型。 強型別會取代介面所宣告<xref:System.Object>的<xref:System.Array>較弱類型, 例如和。

## <a name="how-to-fix-violations"></a>如何修正違規
若要修正此規則的違規, 請明確地執行介面成員 (將它<xref:System.Collections.ICollection.CopyTo%2A>宣告為)。 加入公用強型別成員, 並將`CopyTo`其宣告為, 並讓它接受強型別陣列做為第一個參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
如果您要執行以物件為基礎的新集合 (例如二進位樹狀結構), 而擴充新集合的類型會決定強型別, 請隱藏此規則的警告。 這些類型應符合這項規則, 並公開強型別成員。

## <a name="example"></a>範例
下列範例示範正確的執行<xref:System.Collections.ICollection>方式。

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>相關規則
[CA1038枚舉器應該是強型別](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039清單為強型別](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>