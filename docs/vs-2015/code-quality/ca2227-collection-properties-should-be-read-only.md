---
title: CA2227：集合屬性應該是唯讀的 |Microsoft Docs
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
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658863"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227：集合屬性應該為唯讀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft。使用方式|
|中斷變更|中斷|

## <a name="cause"></a>原因
 外部可見的可寫入屬性是用來執行 <xref:System.Collections.ICollection?displayProperty=fullName> 的類型。 規則會忽略陣列、索引子（名稱為 ' Item ' 的屬性）和許可權集合。

## <a name="rule-description"></a>規則描述
 可寫入的集合屬性允許使用者以完全不同的集合來取代集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。 如果取代集合是目標，則慣用的設計模式是包含方法，以從集合中移除所有專案，並使用方法來重新填入集合。 如需此模式的範例，請參閱 <xref:System.Collections.ArrayList?displayProperty=fullName> 類別的 <xref:System.Collections.ArrayList.Clear%2A> 和 <xref:System.Collections.ArrayList.AddRange%2A> 方法。

 二進位和 XML 序列化都支援集合的唯讀屬性。 @No__t_0 類別對於實 <xref:System.Collections.ICollection> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName> 以可序列化的型別，有特定的需求。

## <a name="how-to-fix-violations"></a>如何修正違規
 若要修正此規則的違規，請將屬性設為唯讀，如果設計需要的話，請新增方法來清除並重新填入集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機
 請勿隱藏此規則的警告。

## <a name="example"></a>範例
 下列範例會顯示具有可寫入集合屬性的類型，並顯示如何直接取代集合。 此外，也會顯示使用 `Clear` 和 `AddRange` 方法來取代唯讀集合屬性的慣用方式。

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>相關規則
 [CA1819：屬性不應該傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)
