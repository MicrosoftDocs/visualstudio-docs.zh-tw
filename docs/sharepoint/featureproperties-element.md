---
title: FeatureProperties 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb345e66a53f9816281df6e948a8961252c0fcea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862585"
---
# <a name="featureproperties-element"></a>FeatureProperties 項目
  它會部署到 SharePoint 時，會包含與功能的屬性值的集合。 將功能部署之後，您可以在程式碼中存取的屬性值。  
  
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
|[FeatureProperty](../sharepoint/featureproperty-element.md)|選擇性項目。<br /><br /> 表示自訂屬性索引鍵/值格式。|  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目必要的根元素的`.spdata`檔案。|  
  
## <a name="remarks"></a>備註  
 如需有關功能屬性的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>項目資訊
  
|元素|描述|  
|-------------|-----------------|  
|**命名空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔案**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
 [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
