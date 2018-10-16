---
title: Xml (XElement 動態屬性) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6daf831030fd02f3aa1e3a4844a42ba60bf0574c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175808"
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
 [XElement 類別動態屬性](../designers/xelement-class-dynamic-properties.md)   
 [值](../designers/value-xelement-dynamic-property.md)



