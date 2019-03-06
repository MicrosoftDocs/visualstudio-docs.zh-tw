---
title: ExtensionDataItem 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 969c82152c1e781da83fe4da20e49fdcf8dda375
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617050"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 項目
  自訂資料項目中索引鍵/值格式的 SharePoint 專案項目與相關聯。 金鑰和值必須是字串。

## <a name="syntax"></a>語法

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**Key**|所需**xs： 字串**屬性。<br /><br /> 用來儲存和擷取的資料項目的索引鍵。|
|**值**|所需**xs: string**屬性。<br /><br /> 資料項目的值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|代表 SharePoint 專案項目相關聯的自訂資料項目的集合。|

## <a name="remarks"></a>備註
 當您自訂的資料使用與相關聯的 SharePoint 專案項目<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>的屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件時，Visual Studio 會將資料儲存至新**ExtensionDataItem**中的項目`.spdata`檔案專案項目。 如需詳細資訊，請參閱 <<c0> [ 將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
