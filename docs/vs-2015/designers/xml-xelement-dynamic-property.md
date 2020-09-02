---
title: Xml (XElement 動態屬性) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663838"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (XElement 動態屬性)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

取得項目未格式化的 XML 內容。

## <a name="syntax"></a>語法

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>屬性值/傳回值
 表示項目未格式化 XML 內容的 <xref:System.String>。

## <a name="remarks"></a>備註
 這個屬性等同於 <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> 類別的 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。

## <a name="see-also"></a>另請參閱
 [System.xml.linq.xelement> 類別動態屬性](../designers/xelement-class-dynamic-properties.md)[值](../designers/value-xelement-dynamic-property.md)
