---
title: 專案專案元素 |Microsoft Docs
description: 取得專案專案專案的參考資訊，代表 SharePoint 專案專案 XML 架構參考中的 SharePoint 專案專案。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e211aa44b1402d6667fc3e02ca7e271a29c3ec7
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305050"
---
# <a name="projectitem-element"></a>ProjectItem 項目
  表示 SharePoint 專案專案。 這個元素是 *.spdata* 檔案的必要根項目。

## <a name="syntax"></a>Syntax

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**DefaultFile**|選擇性 **xs： string** 屬性。<br /><br /> 當您在 **方案總管** 中開啟 SharePoint 專案專案時，在 Visual Studio 編輯器中開啟之檔案的相對路徑，包括檔案名。 路徑是相對於包含 *.spdata* 檔案的資料夾。|
|**FeatureReceiverClass**|選擇性 **xs： string** 屬性。<br /><br /> 這個 SharePoint 專案專案之功能接收器類別的完整名稱。 如需功能接收器的詳細資訊，請參閱 [在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|
|**FeatureReceiverAssembly**|選擇性 **xs： string** 屬性。<br /><br /> 指定元件的完整名稱，該元件定義此 SharePoint 專案專案的功能接收器。 如需功能接收器的詳細資訊，請參閱 [在專案專案中提供封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。 如需完整元件名稱的詳細資訊，請參閱 [元件名稱](/dotnet/framework/app-domains/assembly-names)。|
|**SupportedTrustLevels**|選擇性 **xs： string** 屬性。<br /><br /> 指定這個 SharePoint 專案專案支援的信任層級。 這個值可以是下列其中一個字串：沙箱化、FullTrust 或全部。 All 值會同時指定沙箱和 FullTrust。<br /><br /> 在自訂 SharePoint 專案專案類型中，這個屬性的值會對應至您 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 在方法的實值中指派給屬性的值 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 。 如果您為這個屬性指定不同的值，Visual Studio 會覆寫值，讓它指定您在屬性中指定的相同信任層級 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 。|
|**SupportedDeploymentScopes**|選擇性 **xs： string** 屬性。<br /><br /> 指定這個 SharePoint 專案專案支援的部署範圍。 這個值是以逗號分隔的字串，由下列一或多個字串組成： Farm、Site、Web、WebApplication 或 Package。 例如：`Web, Site`<br /><br /> 在自訂 SharePoint 專案專案類型中，這個屬性的值會對應至您 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 在方法的實值中指派給屬性的值 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 。 如果您為這個屬性指定不同的值，Visual Studio 會覆寫值，讓它指定您在屬性中指定的相同信任層級 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 。|
|**型別**|必要的 **xs： string** 屬性。<br /><br /> SharePoint 專案專案的識別碼。 在自訂 SharePoint 專案專案類型中，識別碼是您傳遞給的字串 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> 。 如需詳細資訊，請參閱 [如何：定義 SharePoint 專案專案類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。<br /><br /> 如需 Visual Studio 中隨附之內建 SharePoint 專案專案的識別碼清單，請參閱 [擴充 SharePoint 專案專案](../sharepoint/extending-sharepoint-project-items.md)。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|選擇性項目。<br /><br /> 表示與 SharePoint 專案專案相關聯的自訂資料項目集合。<br /><br /> 您只能包含一個 **ExtensionData** 元素。|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|選擇性項目。<br /><br /> 表示將功能部署至 SharePoint 時包含的屬性值集合。<br /><br /> 您只能包含一個 **FeatureProperties** 元素。|
|[檔案](../sharepoint/files-element.md)|選擇性的 **FileCollectionType** 元素。<br /><br /> 使用 SharePoint 專案專案指定要部署的檔案，例如功能元素檔和相依非 SharePoint 專案的輸出。<br /><br /> 包含 **檔案或** **ProjectItemFolder** 元素，但不能同時包含兩者。|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|選擇性的 **ProjectItemFolderType** 元素。<br /><br /> 表示對應的資料夾。<br /><br /> 包含 **檔案或** **ProjectItemFolder** 元素，但不能同時包含兩者。|
|[SafeControls](../sharepoint/safecontrols-element.md)|選擇性項目。<br /><br /> 代表 ASPX 控制項和 Web 組件的集合，這些控制項和在 SharePoint 網站上的任何 ASPX 頁面上都被指定為安全的使用者。<br /><br /> 您只能包含一個 **SafeControls** 元素。|

### <a name="parent-elements"></a>父元素
 無。

## <a name="element-information"></a>項目資訊

|屬性|值|
|-|-|
|**Namespace**|HTTP： \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**結構描述名稱**|SharePoint 專案專案架構|
|**驗證檔**|ProjectItemModelSchema .xsd|
|**可以是空的**|否|

## <a name="see-also"></a>另請參閱
[SharePoint 專案專案架構 rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
