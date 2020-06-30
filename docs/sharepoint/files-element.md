---
title: Files 元素 |Microsoft Docs
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
ms.openlocfilehash: 42e919bbe25047da14940203ac86793430aeadde
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546506"
---
# <a name="files-element"></a>Files 項目
  指定要與 SharePoint 專案專案一起部署的檔案，例如功能元素檔和相依非 SharePoint 專案的輸出。

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
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|選擇性的**ProjectItemFileType**元素。<br /><br /> 代表在部署至 SharePoint 時，要包含在專案專案中的 SharePoint 檔案（例如功能元素檔案）。|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|選擇性的**ProjectOutputFileType**元素。<br /><br /> 代表專案部署至 SharePoint 時，要包含在專案專案中的輸出。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是檔案的必要根項目 `.spdata` 。|

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
