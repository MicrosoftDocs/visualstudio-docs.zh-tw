---
title: CA2227:集合屬性應該為唯讀
ms.date: 09/28/2018
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
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: be864812cc7355f80700bd3e270178c9626d4180
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305906"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227:集合屬性應該為唯讀

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft.Usage|
|重大變更|中斷|

## <a name="cause"></a>原因

外部可見、可寫入的屬性屬於實 <xref:System.Collections.ICollection?displayProperty=fullName> 的類型。 此規則會忽略陣列、索引子（名稱為 ' Item ' 的屬性）和許可權集合。

## <a name="rule-description"></a>規則描述

可寫入的集合屬性允許使用者以完全不同的集合來取代集合。 唯讀屬性會阻止集合被取代，但仍然允許設定個別成員。 如果取代集合是目標，則慣用的設計模式是包含從集合中移除所有專案的方法，以及重新擴展集合的方法。 如需此模式的範例，請參閱 @no__t 2 類別的 <xref:System.Collections.ArrayList.Clear%2A> 和 @no__t 1 方法。

二進位和 XML 序列化都支援集合的唯讀屬性。 @No__t-0 類別對於實 <xref:System.Collections.ICollection> 和 <xref:System.Collections.IEnumerable?displayProperty=fullName> 的型別有特定的需求，以便可序列化。

## <a name="how-to-fix-violations"></a>如何修正違規

若要修正此規則的違規情形，請將屬性設為唯讀。 如果設計需要，請新增方法來清除和重新擴展集合。

## <a name="when-to-suppress-warnings"></a>隱藏警告的時機

如果屬性是[資料傳輸物件（DTO）](/previous-versions/msp-n-p/ff649585(v=pandp.10))類別的一部分，您可以隱藏警告。

否則，請勿隱藏此規則的警告。

## <a name="example"></a>範例

下列範例會顯示具有可寫入集合屬性的類型，並顯示如何直接取代集合。 此外，它也會顯示使用 `Clear` 和 @no__t 1 方法來取代唯讀集合屬性的慣用方式。

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>相關規則

- [CA1819：屬性不應傳回陣列 @ no__t-0