---
title: Value (XAttribute 動態屬性) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664055"
---
# <a name="value-xattribute-dynamic-property"></a>Value (XAttribute 動態屬性)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取得或設定 XML 屬性的值。

## <a name="syntax"></a>語法

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 包含此屬性之值的 <xref:System.String>。

## <a name="exceptions"></a>例外狀況

|例外狀況類型|條件|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|設定時，`value` 為 `null`。|

## <a name="remarks"></a>備註
 此屬性相當於 <xref:System.Xml.Linq.XAttribute.Value%2A> 類別的 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 屬性，但此動態屬性也支援變更通知。

## <a name="see-also"></a>另請參閱
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[System.xml.linq.xattribute> 類別動態屬性](../designers/xattribute-class-dynamic-properties.md)[屬性](../designers/attribute-xelement-dynamic-property.md)
