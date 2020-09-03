---
title: CA2227：集合屬性應為唯讀 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540526"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227:集合屬性應該為唯讀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|值|
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|類別|Microsoft. 使用量|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的可寫入屬性是實作為的型別 <xref:System.Collections.ICollection?displayProperty=fullName> 。 規則會忽略陣列、索引子 (名稱為 ' Item ' ) 的屬性和許可權集合。

## <a name="rule-description"></a>規則描述
 可寫入的集合屬性允許使用者以完全不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。 如果將集合取代為目標，則慣用的設計模式是包含方法，以移除集合中的所有元素，以及重新填入集合的方法。 如需 <xref:System.Collections.ArrayList.Clear%2A> 此模式的範例，請參閱類別的和 <xref:System.Collections.ArrayList.AddRange%2A> 方法 <xref:System.Collections.ArrayList?displayProperty=fullName> 。

 二進位和 XML 序列化都支援做為集合的唯讀屬性。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別具有實作為或可序列化之類型的特定需求 <xref:System.Collections.ICollection> <xref:System.Collections.IEnumerable?displayProperty=fullName> 。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規情形，請將屬性設為唯讀，如果設計需要的話，請新增方法來清除和重新填入集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示具有可寫入集合屬性的型別，並顯示如何直接取代該集合。 此外， `Clear` 也會顯示使用和方法來取代唯讀集合屬性的慣用方法 `AddRange` 。

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1819:屬性不應該傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)
