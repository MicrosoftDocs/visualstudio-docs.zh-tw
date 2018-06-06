---
title: SafeControls 項目 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 85b0d1884812c4846d78804b34d50986140bf29e
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692024"
---
# <a name="safecontrols-element"></a>SafeControls 項目
  ASPX 控制項和網頁組件所指定的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面為安全的集合。  
  
## <a name="syntax"></a>語法  
  
```xml  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|選擇性項目。<br /><br /> 代表 ASPX 控制項或指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面的 Web 組件。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目為必要的根元素的`.spdata`檔案。|  
  
## <a name="remarks"></a>備註  
 如需安全控制項的詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊  
  
|||  
|-|-|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱  
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  