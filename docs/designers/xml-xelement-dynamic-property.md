---
title: "Xml (XElement 動態屬性) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
apiname: XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b03c03ce5980b1c6042d1670d33d43fea6c7edc4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xml-xelement-dynamic-property"></a>Xml (XElement 動態屬性)
取得項目未格式化的 XML 內容。  
  
## <a name="syntax"></a>語法  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 表示項目未格式化 XML 內容的 <xref:System.String>。  
  
## <a name="remarks"></a>備註  
 這個屬性等同於 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 類別的 <xref:System.Xml.Linq.XNode?displayProperty=fullName> 方法，且 `SaveOptions` 參數設定為 <xref:System.Xml.Linq.SaveOptions>。  
  
## <a name="see-also"></a>請參閱  
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xelement-dynamic-property.md)