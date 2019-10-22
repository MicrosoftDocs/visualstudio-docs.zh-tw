---
title: Element (XElement 動態屬性)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637329"
---
# <a name="element-xelement-dynamic-property"></a>Element (XElement 動態屬性)

取得用於擷取對應於指定擴充名稱之子項目執行個體的索引子 (Indexer)。

## <a name="syntax"></a>語法

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

`XElement Item(String expandedName)` 型別的索引子。 如果沒有具有指定之名稱的項目，這個索引子會採用擴充名稱參數，並傳回對應的 <xref:System.Xml.Linq.XElement> 或 `null`。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XContainer.Element%2A> 類別的 <xref:System.Xml.Linq.XContainer?displayProperty=fullName> 方法。

## <a name="see-also"></a>請參閱

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [XElement 類別動態屬性](../designers/attribute-xelement-dynamic-property.md)
- [項目](../designers/elements-xelement-dynamic-property.md)