---
title: "ProjectItemFolder 項目 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: ProjectItemFolder element
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c6b5c895f36f3e0b040ce1e3db7cb87cd52e5b9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 項目
  表示對應的資料夾。  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>類型  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**Target**|需要**xs: string**屬性。<br /><br /> SharePoint 安裝對應的資料夾對應，相對於部署根資料夾中的資料夾路徑。 部署根資料夾由所指定之部署類型**類型**屬性。<br /><br /> 如需詳細資訊，請參閱說明**部署路徑**和**部署根**屬性的 SharePoint 專案中的項目[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|需要**xs: string**屬性。<br /><br /> 為對應的資料夾部署的類型。 如需可能值的詳細資訊，請參閱描述**部署類型**屬性中的 SharePoint 專案項目的[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這是必要的根元素的.spdata 檔案。|  
  
## <a name="remarks"></a>備註  
 如需對應的資料夾的詳細資訊，請參閱[如何： 新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**命名空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [如何：新增與移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  