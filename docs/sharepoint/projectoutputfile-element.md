---
title: "ProjectOutputFile 項目 |Microsoft 文件"
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
helpviewer_keywords: ProjectOutputFile element
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a397648dd81ead8134777c8b36982fa6b65b687b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 項目
  表示要部署至 SharePoint 時，包含與專案項目個別專案的輸出。  
  
## <a name="syntax"></a>語法  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>類型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|**ProjectId**|需要**xs: string**屬性。<br /><br /> 相依專案具有您想要包含的輸出的 GUID。 這會對應至**ProjectGuid**相依專案檔中的項目。|  
|**ProjectPath**|需要**xs: string**屬性。<br /><br /> 相對路徑，包括相依專案具有您想要包含的輸出的專案檔案名稱。 這個路徑是相對於包含 SharePoint 專案項目之 SharePoint 專案的根資料夾。|  
|**Target**|選擇性**xs: string**屬性。<br /><br /> 相依專案輸出到部署在 SharePoint 伺服器上，相對於部署根資料夾的所在路徑。 部署根資料夾由所指定之部署類型**類型**屬性。<br /><br /> 如需詳細資訊，請參閱說明**部署路徑**和**部署根**屬性的 SharePoint 專案中的項目[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|需要**xs: string**屬性。<br /><br /> 部署到相依專案的輸出使用的型別。 如需可能值的詳細資訊，請參閱描述**部署類型**屬性中的 SharePoint 專案項目的[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[檔案](../sharepoint/files-element.md)|指定要部署至 SharePoint 時，與 SharePoint 專案項目包含的檔案。|  
  
## <a name="remarks"></a>備註  
 使用**ProjectOutputFile**要部署的 SharePoint 專案項目中包含專案的輸出項目。 您可以指定不同的專案或相同專案包含的專案項目。 如需詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)  
  
  