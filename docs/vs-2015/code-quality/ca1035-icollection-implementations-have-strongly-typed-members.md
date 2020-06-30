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
ms.openlocfilehash: 2e679fb3cc62ba80cfb7b56dfd7fa6590375565e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546610"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035:ICollection 的實作有強類型成員
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|類別|Microsoft. Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護的類型 <xref:System.Collections.ICollection?displayProperty=fullName> 會執行，但不會提供的強型別方法 <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> 。 強型別版本的 <xref:System.Collections.ICollection.CopyTo%2A> 必須接受兩個參數，而且不能有 <xref:System.Array?displayProperty=fullName> 或陣列做 <xref:System.Object?displayProperty=fullName> 為它的第一個參數。

## <a name="rule-description"></a>規則描述
 這項規則需要 <xref:System.Collections.ICollection> 提供強型別成員，讓使用者在 <xref:System.Object> 使用介面所提供的功能時，不需要將引數轉換成型別。 此規則假設執行的型別 <xref:System.Collections.ICollection> 會管理型別實例的集合，而該類型比更強 <xref:System.Object> 。

 <xref:System.Collections.ICollection> 會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。 如果集合中的物件擴充 <xref:System.ValueType?displayProperty=fullName> ，您必須提供的強型別成員， <xref:System.Collections.IEnumerable.GetEnumerator%2A> 以避免因裝箱而造成的效能降低。 當集合的物件為參考型別時，這不是必要的。

 若要執行介面成員的強型別版本，請使用表單中的名稱（例如）來明確地執行介面成員 `InterfaceName.InterfaceMemberName` <xref:System.Collections.ICollection.CopyTo%2A> 。 明確的介面成員會使用介面所宣告的資料類型。 使用介面成員名稱（例如）來執行強型別成員 <xref:System.Collections.ICollection.CopyTo%2A> 。 將強型別成員宣告為 public，並將參數和傳回值宣告為集合所管理的強式類型。 強型別會取代介面所宣告的較弱類型 <xref:System.Object> ，例如和 <xref:System.Array> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請明確地執行介面成員（將它宣告為 <xref:System.Collections.ICollection.CopyTo%2A> ）。 加入公用強型別成員，並將 `CopyTo` 其宣告為，並讓它接受強型別陣列做為第一個參數。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 如果您要執行以物件為基礎的新集合（例如二進位樹狀結構），而擴充新集合的類型會決定強型別，請隱藏此規則的警告。 這些類型應符合這項規則，並公開強型別成員。

## <a name="example"></a>範例
 下列範例示範正確的執行方式 <xref:System.Collections.ICollection> 。

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>相關規則
 [CA1038:列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039:清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
