---
title: "CA1035: ICollection 實作包含強類型成員 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3e595046442092c11b068b6df6fde2a9a56e705
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035：ICollection 實作包含強類型成員
|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## <a name="cause"></a>原因  
 公用或受保護的型別會實作<xref:System.Collections.ICollection?displayProperty=fullName>，但不是提供強型別的方法<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>。 強類型的版本<xref:System.Collections.ICollection.CopyTo%2A>必須接受兩個參數，而且不能有<xref:System.Array?displayProperty=fullName>或陣列<xref:System.Object?displayProperty=fullName>做為其第一個參數。  
  
## <a name="rule-description"></a>規則描述  
 這項規則要求<xref:System.Collections.ICollection>實作提供強類型成員，如此使用者不需將引數轉換<xref:System.Object>輸入使用介面所提供的功能時。 這項規則假設的實作類型<xref:System.Collections.ICollection>因此來管理比更強型別的執行個體的集合<xref:System.Object>。  
  
 <xref:System.Collections.ICollection> 會實作 <xref:System.Collections.IEnumerable?displayProperty=fullName> 介面。 如果集合中的物件延伸<xref:System.ValueType?displayProperty=fullName>，您必須提供強類型的成員<xref:System.Collections.IEnumerable.GetEnumerator%2A>以避免 boxing 所造成的效能降低。 當集合的物件參考型別時，這是不需要。  
  
 若要實作介面成員的強類型的版本，來實作介面成員明確地在表單中使用名稱`InterfaceName.InterfaceMemberName`，例如<xref:System.Collections.ICollection.CopyTo%2A>。 明確介面成員會使用介面所宣告的資料類型。 實作強類型的成員所使用的介面成員名稱，例如<xref:System.Collections.ICollection.CopyTo%2A>。 宣告為公用，強類型的成員宣告的參數和傳回值都由集合所管理的強型別。 強式型別取代較弱的類型例如<xref:System.Object>和<xref:System.Array>介面所宣告的。  
  
## <a name="how-to-fix-violations"></a>如何修正違規  
 若要修正此規則的違規情形，實作介面成員明確 (將它宣告為<xref:System.Collections.ICollection.CopyTo%2A>)。 新增公用的強類型的成員，宣告為`CopyTo`，並且做為其第一個參數的強類型的陣列。  
  
## <a name="when-to-suppress-warnings"></a>隱藏警告的時機  
 如果您實作新的物件架構集合，例如二進位樹狀目錄中，擴充新集合的型別決定強型別，則隱藏此規則的警告。 這些類型應該符合此規則，並公開強類型的成員。  
  
## <a name="example"></a>範例  
 下列範例會示範正確的方式來實作<xref:System.Collections.ICollection>。  
  
 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## <a name="related-rules"></a>相關的規則  
 [CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>