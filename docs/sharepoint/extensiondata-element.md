---
title: ExtensionData 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbbd291888c9df1875afed64de034ab070ce8ef6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608314"
---
# <a name="extensiondata-element"></a>ExtensionData 項目
  代表 SharePoint 專案項目相關聯的自訂資料項目的集合。

## <a name="syntax"></a>語法

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|選擇性項目。<br /><br /> 表示索引鍵/值格式中的 SharePoint 專案項目相關聯的自訂資料項目。 金鑰和值必須是字串。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目必要的根元素的`.spdata`檔案。|

## <a name="remarks"></a>備註
 當您自訂的資料使用與相關聯的 SharePoint 專案項目<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>的屬性<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>物件時，Visual Studio 會儲存的資料**ExtensionData**中的項目`.spdata`專案檔項目。 如需詳細資訊，請參閱 <<c0> [ 將資料儲存於 SharePoint 專案系統擴充](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
