---
title: CA1039：清單為強類型
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 961052d778551818942977b4d8895b85e96091d6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551817"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039：清單為強類型

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|類別|Microsoft.Design|
|中斷變更|中斷|

## <a name="cause"></a>原因

公用或受保護的型別會實作<xref:System.Collections.IList?displayProperty=fullName>，但不提供強型別的方法的一個或多個項目：

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>規則描述

此規則需要<xref:System.Collections.IList>實作提供強類型成員，以便使用者不需要引數轉換<xref:System.Object?displayProperty=fullName>輸入使用時，就提供的功能介面。 <xref:System.Collections.IList>可依索引存取的物件的集合會實作介面。 這項規則假設，實作型別<xref:System.Collections.IList>可管理比更強型別的執行個體的一群<xref:System.Object>。

<xref:System.Collections.IList> 會實作<xref:System.Collections.ICollection?displayProperty=fullName>和<xref:System.Collections.IEnumerable?displayProperty=fullName>介面。 如果您實作<xref:System.Collections.IList>，您必須提供必要的強型別的成員的<xref:System.Collections.ICollection>。 如果在集合中的物件延伸<xref:System.ValueType?displayProperty=fullName>，您必須提供強型別的成員<xref:System.Collections.IEnumerable.GetEnumerator%2A>以避免效能降低，起因於 boxing; 這不是必要的物件集合的參考型別時。

若要符合此規則，來實作介面成員明確 InterfaceName.InterfaceMemberName，表單中使用名稱，例如<xref:System.Collections.IList.Add%2A>。 明確介面成員會使用介面所宣告的資料類型。 藉由使用介面成員名稱，例如實作強型別的成員`Add`。 宣告為公用，強類型的成員宣告的參數和傳回值都由集合所管理的強型別。 強式型別取代較弱的類型這類<xref:System.Object>和<xref:System.Array>介面所宣告的。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，明確地實作<xref:System.Collections.IList>成員，並提供強型別替代項目，如先前所記下的成員。 正確實作的程式碼<xref:System.Collections.IList>介面並提供必要強類型的成員，請參閱下列的範例。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 當您實作新的物件架構集合，例如連結的清單中，擴充新集合的型別決定的強型別時，請隱藏此規則的警告。 這些類型應該符合此規則，並公開強類型的成員。

## <a name="example"></a>範例
 在下列範例中，型別`YourType`擴充<xref:System.Collections.CollectionBase?displayProperty=fullName>，如同所有的強類型的集合。 <xref:System.Collections.CollectionBase> 提供明確的實作<xref:System.Collections.IList>為您的介面。 因此，您必須只提供強型別的成員<xref:System.Collections.IList>和<xref:System.Collections.ICollection>。

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>相關的規則
 [CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>