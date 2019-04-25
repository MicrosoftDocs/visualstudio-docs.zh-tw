---
title: Xml (XElement 動態屬性)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843949"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (XElement 動態屬性)

取得項目未格式化的 XML 內容。

## <a name="syntax"></a>語法

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值

表示項目未格式化 XML 內容的 <xref:System.String>。

## <a name="remarks"></a>備註

這個屬性等同於 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 類別的 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。

## <a name="see-also"></a>另請參閱

- [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)
- [值](../designers/value-xelement-dynamic-property.md)