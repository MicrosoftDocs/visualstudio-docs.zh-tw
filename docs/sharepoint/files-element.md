---
title: 檔案項目 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 330c408aa0e283eb282b93f77726ccc5d9547795
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766902"
---
# <a name="files-element"></a>Files 項目
  指定要部署的 SharePoint 專案項目，例如功能項目檔案，以及相依的非 SharePoint 專案的輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```xml  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>類型  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素
  
|項目|描述|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|選擇性**ProjectItemFileType**項目。<br /><br /> 代表 SharePoint 檔案，例如功能項目檔中，以部署至 SharePoint 時，包含與專案項目。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|選擇性**ProjectOutputFileType**項目。<br /><br /> 表示要部署至 SharePoint 時，與專案項目包含專案的輸出。|  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目為必要的根元素的`.spdata`檔案。|  
  
## <a name="element-information"></a>項目資訊
  
|||  
|-|-|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
