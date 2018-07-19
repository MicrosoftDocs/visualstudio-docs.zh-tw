---
title: SharePoint 專案項目結構描述參考 |Microsoft Docs
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
ms.openlocfilehash: b94856d4e00cd15f324040ccd49c90bb1be29a7d
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118593"
---
# <a name="sharepoint-project-item-schema-reference"></a>SharePoint 專案項目結構描述參考
  Visual Studio 會使用 SharePoint 專案項目結構描述驗證的內容 *.spdata*檔案。 *.Spdata*檔案指定的內容和行為的 SharePoint 專案項目。 如需詳細的 SharePoint 專案項目內容的相關資訊，請參閱[建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)。  
  
 SharePoint 專案項目結構描述名為 ProjectItemModelSchema.xsd 和已安裝預設會在 %Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas。  
  
 根項目是[ProjectItem](../sharepoint/projectitem-element.md)項目。 下表描述所有的結構描述所定義的項目。  
  
|元素|描述|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|代表 SharePoint 專案項目相關聯的自訂資料項目的集合。|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|表示索引鍵/值格式中的 SharePoint 專案項目相關聯的自訂資料項目。 金鑰和值必須是字串。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|表示它會部署到 SharePoint 時，會包含與功能的屬性值的集合。 將功能部署之後，您可以在程式碼中存取的屬性值。|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|表示它會部署到 SharePoint 時，會包含與功能的自訂屬性。 將功能部署之後，您可以在程式碼中存取屬性。|  
|[檔案](../sharepoint/files-element.md)|指定要部署與 SharePoint 專案項目，例如功能元素檔案或專案的輸出檔案。|  
|[專案項目](../sharepoint/projectitem-element.md)|代表 SharePoint 專案項目。|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|代表功能項目檔案，以包含與專案項目時將它部署至 SharePoint 的 SharePoint 檔案。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|表示對應的資料夾。|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|表示要加入的專案項目時將它部署至 SharePoint 專案的輸出。|  
|[SafeControl](../sharepoint/safecontrol-element.md)|代表 ASPX 控制項或指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面上的 Web 組件。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|代表 ASPX 控制項和被指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面上的 Web 組件的集合。|  
  
## <a name="see-also"></a>另請參閱
 [建立項目範本和專案範本，為 SharePoint 專案項目](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)  
  
