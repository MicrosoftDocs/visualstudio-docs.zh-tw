---
title: ProjectItemFile 元素 |Microsoft Docs
description: 取得 ProjectItemFile 元素的參考資訊，代表 SharePoint 專案專案 XML 架構參考中的專案專案檔。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 099f20926487b09240219f04d9bce4a79709f6e6
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440801"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 項目
  表示當專案專案部署至 SharePoint 時，要包含在專案專案中的 SharePoint 檔案，例如功能元素檔。

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
|**Source**|必要的 **xs： string** 屬性。<br /><br /> 要與專案專案一起部署的檔案名。|
|**Target**|選擇性 **xs： string** 屬性。<br /><br /> 將在 SharePoint 上部署檔案的路徑（相對於部署根資料夾）。 部署根資料夾取決於 **type** 屬性所指定的部署類型。 如果未指定 **目標** 屬性，則會將檔案部署到 [ **來源** ] 屬性中指定之名稱的資料夾。<br /><br /> 如需詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案的 **部署路徑** 和 **部署根** 屬性的說明。|
|**型別**|必要的 **xs： string** 屬性。<br /><br /> 檔案的部署類型。 如需可能值的詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 專案專案的 [**部署類型**] 屬性的描述。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[檔案](../sharepoint/files-element.md)|指定當 SharePoint 專案專案部署至 SharePoint 時要包含的檔案。|

## <a name="remarks"></a>備註
 通常會在 **ProjectItemFile** 元素中參考的 SharePoint 檔案包括功能專案檔 (*Elements.xml*) 、清單定義 (*Schema.xml*) 的架構檔案，以及 Web 組件 () 的 Web 元件定義 *檔。*

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案專案架構|
|**驗證檔**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
