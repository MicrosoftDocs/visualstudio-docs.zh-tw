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
ms.openlocfilehash: d75041c1b0202eecd5769773efbcfce9c53ec4ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="files-element"></a>Files 項目
  指定要部署的 SharePoint 專案項目，例如功能項目檔案，以及相依的非 SharePoint 專案的輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>類型  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|選擇性**ProjectItemFileType**項目。<br /><br /> 代表 SharePoint 檔案，例如功能項目檔中，以部署至 SharePoint 時，包含與專案項目。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|選擇性**ProjectOutputFileType**項目。<br /><br /> 表示要部署至 SharePoint 時，與專案項目包含專案的輸出。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這是必要的根元素的.spdata 檔案。|  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**命名空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  