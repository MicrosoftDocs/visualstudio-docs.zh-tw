---
title: CA2227： 集合屬性應該為唯讀 |Microsoft Docs
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
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1db0ab6bae6a374726e953e505247896864c7f0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830440"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227：集合屬性應該為唯讀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的可寫入屬性是類型可實作<xref:System.Collections.ICollection?displayProperty=fullName>。 此規則會忽略陣列、 索引子 （屬性與名稱為 'Item'） 和權限集合。

## <a name="rule-description"></a>規則描述
 可寫入的集合屬性可讓使用者取代完全不同的集合中的集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。 取代集合為目標，如果 「 慣用的設計模式是包含方法移除集合中的所有項目並重新填入集合的方法。 請參閱<xref:System.Collections.ArrayList.Clear%2A>並<xref:System.Collections.ArrayList.AddRange%2A>方法<xref:System.Collections.ArrayList?displayProperty=fullName>類別，如需此模式的範例。

 二進位與 XML 序列化支援是集合的唯讀屬性。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別具有特定需求的類型可實作<xref:System.Collections.ICollection>和<xref:System.Collections.IEnumerable?displayProperty=fullName>才能序列化。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，將屬性設為唯讀並視設計上有需要，新增方法以清除並重新填入集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示具有一個可寫入的集合屬性的型別，並顯示如何直接取代集合。 此外，慣用的方式來取代資料唯讀集合的屬性使用的`Clear`和`AddRange`方法會顯示。

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>相關的規則
 [CA1819：屬性不應該傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)



