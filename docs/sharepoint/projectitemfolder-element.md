---
title: ProjectItemFolder 元素 |Microsoft Docs
description: 取得 ProjectItemFolder 元素的參考資訊，代表 SharePoint 專案專案 XML 架構參考中的對應資料夾。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d1a5b5086ef90b9d8399a6f0f76bdee77c07288e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950571"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 項目
  表示對應的資料夾。

## <a name="syntax"></a>Syntax

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
|**Target**|必要的 **xs： string** 屬性。<br /><br /> 相對於部署根資料夾，SharePoint 安裝中對應資料夾對應的資料夾路徑。 部署根資料夾取決於 **type** 屬性所指定的部署類型。<br /><br /> 如需詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案的 **部署路徑** 和 **部署根** 屬性的說明。|
|**型別**|必要的 **xs： string** 屬性。<br /><br /> 對應資料夾的部署類型。 如需可能值的詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 專案專案的 [**部署類型**] 屬性的描述。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。 這個元素是 *.spdata* 檔案的必要根項目。|

## <a name="remarks"></a>備註
 如需對應資料夾的詳細資訊，請參閱 [如何：加入和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案專案架構|
|**驗證檔**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [如何：新增和移除對應的資料夾](../sharepoint/how-to-add-and-remove-mapped-folders.md)
