---
title: CA2227：集合屬性應該為唯讀
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: f1bbd3e6ba97d969694e7d2142978c12552b3c50
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860247"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227：集合屬性應該為唯讀

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|分類|Microsoft.Usage|
|中斷變更|中斷|

## <a name="cause"></a>原因

外部可見的可寫入屬性的類型是實作<xref:System.Collections.ICollection?displayProperty=fullName>。 陣列、 索引子 （屬性與名稱為 'Item'） 和權限集合，則會忽略這個規則。

## <a name="rule-description"></a>規則描述

可寫入的集合屬性可讓使用者取代完全不同的集合中的集合。 唯讀屬性會停止該集合會被取代，但是仍允許設定個別的成員。 取代集合為目標，如果 「 慣用的設計模式是包含的方法，從集合移除所有項目和重新匯入集合的方法。 請參閱<xref:System.Collections.ArrayList.Clear%2A>並<xref:System.Collections.ArrayList.AddRange%2A>方法<xref:System.Collections.ArrayList?displayProperty=fullName>類別，如需此模式的範例。

二進位與 XML 序列化支援是集合的唯讀屬性。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>類別具有特定需求的類型可實作<xref:System.Collections.ICollection>和<xref:System.Collections.IEnumerable?displayProperty=fullName>才能序列化。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，將屬性為唯讀。 如果設計上有需要，將方法加入至清除並重新填入集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

您可以隱藏警告，如果屬性是屬於[資料傳輸物件 (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10))類別。

否則，請勿隱藏這項規則的警告。

## <a name="example"></a>範例

下列範例會顯示具有一個可寫入的集合屬性的型別，並顯示如何直接取代集合。 此外，它會顯示的取代唯讀集合的屬性使用偏好的方式`Clear`和`AddRange`方法。

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>相關的規則

- [CA1819：屬性不應該傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)