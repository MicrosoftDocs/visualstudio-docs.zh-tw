---
title: ProjectItemFolder 元素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539811"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 項目
  表示對應的資料夾。

## <a name="syntax"></a>語法

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>類型
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**目標**|必要的**xs： string**屬性。<br /><br /> SharePoint 安裝中對應資料夾相對於部署根資料夾的資料夾路徑。 部署根資料夾取決於**type**屬性所指定的部署類型。<br /><br /> 如需詳細資訊，請參閱[開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案的**部署路徑**和**部署根**屬性的描述。|
|**型別**|必要的**xs： string**屬性。<br /><br /> 對應資料夾的部署類型。 如需可能值的詳細資訊，請參閱[開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案之**部署類型**屬性的描述。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是 *.spdata*檔案的必要根項目。|

## <a name="remarks"></a>備註
 如需對應資料夾的詳細資訊，請參閱[如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)
