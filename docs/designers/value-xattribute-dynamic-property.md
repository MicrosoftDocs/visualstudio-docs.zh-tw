---
title: "Value (XAttribute 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d647e7623820c6621f6605277a695a98454fec5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="value-xattribute-dynamic-property"></a>Value (XAttribute 動態屬性)
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
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute 類別動態屬性](../designers/xattribute-class-dynamic-properties.md)   
 [屬性](../designers/attribute-xelement-dynamic-property.md)