---
title: ProjectItemFile 項目 |Microsoft Docs
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
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322908"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 項目
  代表功能項目檔案，以包含與專案項目時將它部署至 SharePoint 的 SharePoint 檔案。

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
|**來源**|所需**xs: string**屬性。<br /><br /> 要部署的專案項目之檔案的名稱。|
|**Target**|選擇性**xs: string**屬性。<br /><br /> 其中的檔案將部署到 SharePoint，相對於部署根資料夾路徑。 部署根資料夾由所指定之部署類型**型別**屬性。 如果**目標**屬性沒有指定，則檔案會部署至資料夾中指定的名稱與**來源**屬性。<br /><br /> 如需詳細資訊，請參閱描述**部署路徑**並**Deployment Root**屬性的 SharePoint 專案中的項目[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|
|**Type**|所需**xs: string**屬性。<br /><br /> 檔案的部署類型。 如需可能值的詳細資訊，請參閱的描述**部署類型**屬性中的 SharePoint 專案項目的[開發 SharePoint 方案](../sharepoint/developing-sharepoint-solutions.md)。|

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[檔案](../sharepoint/files-element.md)|指定要部署到 SharePoint 時，與 SharePoint 專案項目包含的檔案。|

## <a name="remarks"></a>備註
 通常會參考中的 SharePoint 檔案**ProjectItemFile**項目包含功能項目檔案 (*Elements.xml*)，用於清單定義結構描述檔案 (*Schema.xml*)，以及 Web 組件的 Web 組件定義檔 (*.webpart*)。

## <a name="element-information"></a>項目資訊

|||
|-|-|
|**命名空間**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案項目結構描述|
|**驗證檔案**|ProjectItemModelSchema.xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
- [SharePoint 專案項目結構描述參考](../sharepoint/sharepoint-project-item-schema-reference.md)
