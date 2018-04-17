---
title: SharePoint 專案項目結構描述參考 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b039b1cf31a04a24819b03114c661a3ab1b108a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint 專案項目結構描述參考
  Visual Studio 會使用 SharePoint 專案項目結構描述驗證.spdata 檔案的內容。 .Spdata 檔案指定的內容和 SharePoint 專案項目的行為。 SharePoint 專案項目內容的相關資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 SharePoint 專案項目結構描述為 ProjectItemModelSchema.xsd，並已安裝預設會在 %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas。  
  
 根項目是[ProjectItem](../sharepoint/projectitem-element.md)項目。 下表描述的所有結構描述所定義的項目。  
  
|項目|描述|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|代表 SharePoint 專案項目相關聯的自訂資料項目的集合。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|代表索引鍵/值格式中的 SharePoint 專案項目相關聯的自訂資料項目。 索引鍵和值都必須是字串。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示將它部署至 SharePoint 時，會包含與功能的屬性值的集合。 將功能部署之後，您可以在程式碼中存取屬性值。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|代表將它部署至 SharePoint 時，會包含與功能的自訂屬性。 將功能部署之後，您可以在程式碼中存取屬性。|  
|[檔案](../sharepoint/files-element.md)|指定要部署與 SharePoint 專案項目，例如功能元素檔案或專案的輸出檔案。|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|代表 SharePoint 檔案，例如功能項目檔中，以部署至 SharePoint 時，包含與專案項目。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|表示對應的資料夾。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|表示要部署至 SharePoint 時，與專案項目包含專案的輸出。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|代表 ASPX 控制項或指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面的 Web 組件。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|表示 ASPX 控制項和網頁組件指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面的集合。|  
  
## <a name="see-also"></a>另請參閱  
 [為 SharePoint 專案項目建立項目範本和專案範本](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
  