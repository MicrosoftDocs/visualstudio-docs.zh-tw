---
title: ExtensionDataItem 元素 |Microsoft Docs
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
ms.openlocfilehash: 295ee649cec01e50b237b4fad1798806d460727b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546545"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 項目
  與 SharePoint 專案專案相關聯的自訂資料項目（以索引鍵/值格式）。 索引鍵和值都必須是字串。

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
|**索引鍵**|必要的**xs： string**屬性。<br /><br /> 用來儲存和取出資料項目的索引鍵。|
|**ReplTest1**|必要的**xs： string**屬性。<br /><br /> 資料項目的值。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|代表與 SharePoint 專案專案相關聯之自訂資料項目的集合。|

## <a name="remarks"></a>備註
 當您使用物件的屬性將自訂資料與 SharePoint 專案專案產生關聯時 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> ，Visual Studio 會將資料儲存至專案專案之檔案中的新**ExtensionDataItem**元素 `.spdata` 。 如需詳細資訊，請參閱在[SharePoint 專案系統的延伸模組中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
