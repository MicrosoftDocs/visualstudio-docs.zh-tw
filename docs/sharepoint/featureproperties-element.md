---
title: FeatureProperties 項目 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3b03de87c13744e3b678d4f51e3950352fa2d475
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766710"
---
# <a name="featureproperties-element"></a>FeatureProperties 項目
  部署至 SharePoint 時，會隨附在功能的屬性值的集合。 將功能部署之後，您可以在程式碼中存取屬性值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素
  
|項目|描述|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|選擇性項目。<br /><br /> 代表索引鍵/值格式的自訂屬性。|  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目為必要的根元素的`.spdata`檔案。|  
  
## <a name="remarks"></a>備註  
 如需功能屬性的詳細資訊，請參閱[提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊
  
|元素|描述|  
|-------------|-----------------|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  
