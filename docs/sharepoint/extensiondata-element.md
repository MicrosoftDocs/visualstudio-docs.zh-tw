---
title: ExtensionData 元素 |Microsoft Docs
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
ms.openlocfilehash: 3b700239f97153cef94ab1d7010ad16ed9aa6001
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546558"
---
# <a name="extensiondata-element"></a>ExtensionData 項目
  代表與 SharePoint 專案專案相關聯之自訂資料項目的集合。

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

|元素|描述|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|選擇性項目。<br /><br /> 表示與 SharePoint 專案專案相關聯的自訂資料項目（以索引鍵/值格式）。 索引鍵和值都必須是字串。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是檔案的必要根項目 `.spdata` 。|

## <a name="remarks"></a>備註
 當您使用物件的屬性將自訂資料與 SharePoint 專案專案產生關聯時 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> ，Visual Studio 會將資料儲存至專案專案之檔案中的**ExtensionData**元素 `.spdata` 。 如需詳細資訊，請參閱在[SharePoint 專案系統的延伸模組中儲存資料](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
