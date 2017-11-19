---
title: "SafeControl 項目 |Microsoft 文件"
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
helpviewer_keywords: SafeControl element
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8d9651c320e574c8db9fcafcb6e98f13e45eac1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="safecontrol-element"></a>SafeControl 項目
  代表 ASPX 控制項或指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面的 Web 組件。  
  
## <a name="syntax"></a>語法  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|**Assembly**|選擇性**xs: string**屬性。<br /><br /> 定義在 ASPX 控制項或 Web 組件的組件名稱。 根據預設，這個屬性會使用**$SharePoint.Project.AssemblyFullName$**組件名稱的可取代參數。 如需詳細資訊，請參閱[可置換的參數](../sharepoint/replaceable-parameters.md)。|  
|**IsSafe**|選擇性**xs: boolean**屬性。<br /><br /> 指定在 ASPX 控制項或 Web 組件是不受信任的使用者存取的安全。|  
|**IsSafeAgainstScript**|選擇性**xs: boolean**屬性。<br /><br /> 指定不受信任的使用者可以檢視或編輯在 ASPX 控制項或 Web 組件的內容。|  
|**Name**|選擇性**xs: string**屬性。<br /><br /> 此集合中的安全控制項項目名稱。|  
|**Namespace**|選擇性**xs: string**屬性。<br /><br /> ASPX 控制項或 Web 組件的命名空間。|  
|**類型名稱**|選擇性**xs: string**屬性。<br /><br /> 在 ASPX 控制項或 Web 組件型別名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示 ASPX 控制項和網頁組件指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面的集合。|  
  
## <a name="remarks"></a>備註  
 如需安全控制項的詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  