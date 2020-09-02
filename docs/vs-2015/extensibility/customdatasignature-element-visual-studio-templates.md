---
title: " (Visual Studio 範本的 CustomDataSignature 元素) |Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 784704bea43a87f1aebdc42941906179dca815ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580413"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>CustomDataSignature 項目 (Visual Studio 範本)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

指定要尋找自訂資料的文字簽章。  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<CustomDataSignature>  
  
## <a name="syntax"></a>語法  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的方式。|  
  
## <a name="text-value"></a>文字值  
 需要文字值。  
  
 文字是具有尋找自訂資料所需之文字簽章的字串。  
  
## <a name="remarks"></a>備註  
  是選擇性元素。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)   
 [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
