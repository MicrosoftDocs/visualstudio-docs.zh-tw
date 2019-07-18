---
title: FeatureProperty 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20d24192d8613a4f41d9cdfc04371fb9c9d02076
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967301"
---
# <a name="featureproperty-element"></a>FeatureProperty 項目
  表示它會部署到 SharePoint 時，會包含與功能的自訂屬性。 將功能部署之後，您可以在程式碼中存取屬性。

## <a name="syntax"></a>語法

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**Key**|所需**xs: string**屬性。<br /><br /> 用來儲存和擷取屬性值的索引鍵。 每個屬性必須有此功能中的唯一索引鍵。|
|**值**|所需**xs: string**屬性。<br /><br /> 屬性值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示它會部署到 SharePoint 時，會包含與功能的屬性值的集合。|

## <a name="remarks"></a>備註
 如需有關功能屬性的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
