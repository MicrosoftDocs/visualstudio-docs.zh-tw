---
title: "PreviewImage 項目 （Visual Studio 範本） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e22ff13f9aaffffb22f8b572968376e03796ac9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage 項目 (Visual Studio 範本)
指定的預覽影像，做為檔案名稱，將會出現在 [預覽影像的**新專案**或**加入新項目**] 對話方塊。  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PreviewImage >  
  
## <a name="syntax"></a>語法  
  
```  
<PreviewImage>"filename"</PreviewImage>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義要如何顯示在**新專案**或**加入新項目** 對話方塊。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字必須是字串，表示檔案名稱。  
  
## <a name="remarks"></a>備註  
 `PreviewImage` 是選擇性項目。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)