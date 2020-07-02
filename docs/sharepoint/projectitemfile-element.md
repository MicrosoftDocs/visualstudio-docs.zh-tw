---
title: ProjectItemFile 元素 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c9814498d74a5d1a6533576f1071b4bf7deb57
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539850"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 項目
  代表在部署至 SharePoint 時，要包含在專案專案中的 SharePoint 檔案（例如功能元素檔案）。

## <a name="syntax"></a>語法

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>類型
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**Source**|必要的**xs： string**屬性。<br /><br /> 要與專案專案一起部署的檔案名。|
|**目標**|選擇性的**xs： string**屬性。<br /><br /> 將在 SharePoint 上部署檔案的路徑，相對於部署根資料夾。 部署根資料夾取決於**type**屬性所指定的部署類型。 如果未指定**目標**屬性，則會將檔案部署到具有**Source**屬性中指定之名稱的資料夾。<br /><br /> 如需詳細資訊，請參閱[開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案的**部署路徑**和**部署根**屬性的描述。|
|**型別**|必要的**xs： string**屬性。<br /><br /> 檔案的部署類型。 如需可能值的詳細資訊，請參閱[開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案之**部署類型**屬性的描述。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檔案](../sharepoint/files-element.md)|指定當 SharePoint 專案專案部署至 SharePoint 時，要包含的檔案。|

## <a name="remarks"></a>備註
 通常在**ProjectItemFile**元素中參考的 SharePoint 檔案包含功能專案檔（*Elements.xml*）、清單定義的架構檔案（*Schema.xml*），以及 Web 組件的 Web 元件定義檔（*. webpart*）。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**架構名稱**|SharePoint 專案專案架構|
|**驗證檔案**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
