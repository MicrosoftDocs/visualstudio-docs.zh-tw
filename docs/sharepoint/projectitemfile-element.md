---
title: "ProjectItemFile 項目 |Microsoft 文件"
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
helpviewer_keywords: ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7c222c25417f9a33f28871c94d8dd0d9353e1e76
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile 項目
  代表 SharePoint 檔案，例如功能項目檔中，以部署至 SharePoint 時，包含與專案項目。  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>類型  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**來源**|需要**xs: string**屬性。<br /><br /> 部署專案項目與檔案名稱。|  
|**Target**|選擇性**xs: string**屬性。<br /><br /> 其中的檔案將會部署在 SharePoint，相對於部署根資料夾路徑。 部署根資料夾由所指定之部署類型**類型**屬性。 如果**目標**屬性沒有指定，則檔案會部署至資料夾中指定的名稱與**來源**屬性。<br /><br /> 如需詳細資訊，請參閱說明**部署路徑**和**部署根**屬性的 SharePoint 專案中的項目[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|需要**xs: string**屬性。<br /><br /> 檔案的部署類型。 如需可能值的詳細資訊，請參閱描述**部署類型**屬性中的 SharePoint 專案項目的[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[檔案](../sharepoint/files-element.md)|指定要部署至 SharePoint 時，與 SharePoint 專案項目包含的檔案。|  
  
## <a name="remarks"></a>備註  
 通常會在參考 SharePoint 檔案**ProjectItemFile**元素包括功能的項目檔案 (Elements.xml)、 清單定義 (Schema.xml)，結構描述檔案和 Web 組件 (.webpart) 的 Web 組件定義檔案。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**命名空間**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  