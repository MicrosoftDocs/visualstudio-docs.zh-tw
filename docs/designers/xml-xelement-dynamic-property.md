---
title: Xml (XElement 動態屬性)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cadfd6f02cbe431cb5a74db4a3b7008d05d9c05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026979"
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