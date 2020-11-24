---
title: SharePoint 專案專案架構參考 |Microsoft Docs
description: 請參閱 SharePoint 專案專案 XML 架構參考的總覽 (ProjectItemModelSchema .xsd) ，它是用來驗證 .spdata 檔案的內容。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
- SafeControls element
- SafeControl element
- .spdata files
- ExtensionData element
- FeatureProperties element
- ProjectOutputFile element
- Files element
- ProjectItemFolder element
- ProjectItemFile element
- ExtensionDataItem element
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bd425111e7e3d69e381e69e60daf914f74cd2d11
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442543"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint 專案專案架構參考
  Visual Studio 使用 SharePoint 專案專案架構來驗證 *.spdata* 檔案的內容。 *.Spdata* 檔案會指定 SharePoint 專案專案的內容和行為。 如需 SharePoint 專案專案內容的詳細資訊，請參閱 [建立 sharepoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。

 SharePoint 專案專案架構的名稱為 ProjectItemModelSchema，預設會安裝在% Program Files (x86) % \ Microsoft Visual Studio 11.0 \ Xml\schemas

 根項目是「 [專案專案](../sharepoint/projectitem-element.md) 」元素。 下表描述架構定義的所有元素。

|項目|描述|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|表示與 SharePoint 專案專案相關聯的自訂資料項目集合。|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|表示與 SharePoint 專案專案相關聯的自訂資料項目（以索引鍵/值格式表示）。 索引鍵和值都必須是字串。|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示將功能部署至 SharePoint 時包含的屬性值集合。 部署功能之後，您可以存取程式碼中的屬性值。|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|表示將功能部署至 SharePoint 時隨附的自訂屬性。 部署功能之後，您可以在程式碼中存取屬性。|
|[檔案](../sharepoint/files-element.md)|使用 SharePoint 專案專案指定要部署的檔案，例如功能元素檔或專案的輸出。|
|[ProjectItem](../sharepoint/projectitem-element.md)|表示 SharePoint 專案專案。|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|表示當專案專案部署至 SharePoint 時，要包含在專案專案中的 SharePoint 檔案，例如功能元素檔。|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|表示對應的資料夾。|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|代表專案的輸出，該專案會在專案專案部署至 SharePoint 時包含在專案專案中。|
|[SafeControl](../sharepoint/safecontrol-element.md)|代表在 SharePoint 網站上的任何 ASPX 頁面上，指定為可存取之任何使用者的 ASPX 控制項或網頁元件。|
|[SafeControls](../sharepoint/safecontrols-element.md)|代表 ASPX 控制項和 Web 組件的集合，這些控制項和在 SharePoint 網站上的任何 ASPX 頁面上都被指定為安全的使用者。|

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 專案專案的專案範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
