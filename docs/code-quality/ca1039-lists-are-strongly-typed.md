---
title: CA1039：清單為強類型
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dc14aca81f20a33bce5be99a2ccaf5ccad7d5b0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039：清單為強類型
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|分類|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因
 公用或受保護型別會實作<xref:System.Collections.IList?displayProperty=fullName>但並不提供強型別的方法的一個或多個項目：

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>規則描述
 這項規則要求<xref:System.Collections.IList>實作提供強類型成員，如此使用者不需將引數轉換<xref:System.Object?displayProperty=fullName>輸入使用介面所提供的功能時。 <xref:System.Collections.IList>介面由可依索引存取的物件集合的實作。 這項規則假設的實作類型<xref:System.Collections.IList>此管理比更強型別的執行個體的集合<xref:System.Object>。

 <xref:System.Collections.IList> 實作<xref:System.Collections.ICollection?displayProperty=fullName>和<xref:System.Collections.IEnumerable?displayProperty=fullName>介面。 如果您實作<xref:System.Collections.IList>，您必須提供必要的強類型的成員的<xref:System.Collections.ICollection>。 如果集合中的物件延伸<xref:System.ValueType?displayProperty=fullName>，您必須提供強類型的成員<xref:System.Collections.IEnumerable.GetEnumerator%2A>以避免效能降低 boxing 所造成，這不需要參考型別集合的物件時。

 若要符合此規則，來實作介面成員明確 InterfaceName.InterfaceMemberName，表單中使用的名稱，例如<xref:System.Collections.IList.Add%2A>。 明確介面成員會使用介面所宣告的資料類型。 實作強類型的成員所使用的介面成員名稱，例如`Add`。 宣告為公用，強類型的成員宣告的參數和傳回值都由集合所管理的強型別。 強式型別取代較弱的類型例如<xref:System.Object>和<xref:System.Array>介面所宣告的。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請明確實作<xref:System.Collections.IList>成員，並提供強型別替代項目先前已記錄的成員。 正確實作的程式碼<xref:System.Collections.IList>介面，並提供所需強類型的成員，請參閱下列的範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您實作新的物件架構集合，例如連結的清單中，擴充新集合的型別決定強型別時隱藏此規則的警告。 這些類型應該符合此規則，並公開強類型的成員。

## <a name="example"></a>範例
 在下列範例中，型別`YourType`擴充<xref:System.Collections.CollectionBase?displayProperty=fullName>，如同所有強類型的集合。 請注意，<xref:System.Collections.CollectionBase>提供明確的實作<xref:System.Collections.IList>為您的介面。 因此，您只必須提供強類型的成員<xref:System.Collections.IList>和<xref:System.Collections.ICollection>。

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>另請參閱
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>