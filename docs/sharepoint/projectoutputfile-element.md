---
title: ProjectOutputFile 元素 |Microsoft Docs
description: 取得 ProjectOutputFile 元素的參考資訊，代表 SharePoint 專案專案 XML 架構參考中個別專案的輸出。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffe6f95bdfd7795c837aaaa25ec7ef2a35a7ae76
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442024"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 項目
  表示當專案專案部署至 SharePoint 時，要包含的個別專案的輸出。

## <a name="syntax"></a>語法

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>類型
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**ProjectId**|必要的 **xs： string** 屬性。<br /><br /> 具有您想要包含之輸出的相依專案的 GUID。 這會對應至相依專案檔中的 **ProjectGuid** 元素。|
|**ProjectPath**|必要的 **xs： string** 屬性。<br /><br /> 包含您要包含之輸出的相依專案的相對路徑（包括專案檔名稱）。 此路徑相對於包含 SharePoint 專案專案之 SharePoint 專案的根資料夾。|
|**Target**|選擇性 **xs： string** 屬性。<br /><br /> 要在 SharePoint 伺服器上部署相依專案輸出的路徑（相對於部署根資料夾）。 部署根資料夾取決於 **type** 屬性所指定的部署類型。<br /><br /> 如需詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 sharepoint 專案專案的 **部署路徑** 和 **部署根** 屬性的說明。|
|**型別**|必要的 **xs： string** 屬性。<br /><br /> 要用於相依專案之輸出的部署類型。 如需可能值的詳細資訊，請參閱 [開發 sharepoint 方案](../sharepoint/developing-sharepoint-solutions.md)中 SharePoint 專案專案的 [**部署類型**] 屬性的描述。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[檔案](../sharepoint/files-element.md)|指定當 SharePoint 專案專案部署至 SharePoint 時要包含的檔案。|

## <a name="remarks"></a>備註
 使用 **ProjectOutputFile** 元素，在 SharePoint 專案專案的部署中包含專案的輸出。 您可以指定不同的專案，或包含專案專案的相同專案。 如需詳細資訊，請參閱 [在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案專案架構|
|**驗證檔**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案專案架構參考](../sharepoint/sharepoint-project-item-schema-reference.md)
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)
