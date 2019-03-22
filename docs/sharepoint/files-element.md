---
title: 檔案項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c669b7cc314bc2d7a999e77d5cfb95251789dd8
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323288"
---
# <a name="files-element"></a>Files 項目
  指定要部署使用 SharePoint 專案項目，例如功能項目檔和相依的非 SharePoint 專案的輸出檔案。

## <a name="syntax"></a>語法

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>類型
 **FileCollectionType**

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|選擇性**ProjectItemFileType**項目。<br /><br /> 代表功能項目檔案，以包含與專案項目時將它部署至 SharePoint 的 SharePoint 檔案。|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|選擇性**ProjectOutputFileType**項目。<br /><br /> 表示要加入的專案項目時將它部署至 SharePoint 專案的輸出。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。 這個項目必要的根元素的`.spdata`檔案。|

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
