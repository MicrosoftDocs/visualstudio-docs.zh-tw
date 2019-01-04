---
title: ProjectItem 項目 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7c9a32a7fa84d8adc064aa3a3ac035999295791
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890098"
---
# <a name="projectitem-element"></a>ProjectItem 項目
  代表 SharePoint 專案項目。 這個項目必要的根元素的 *.spdata*檔案。  
  
## <a name="syntax"></a>語法  
  
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
|**DefaultFile**|選擇性**xs： 字串**屬性。<br /><br /> 相對路徑，包括檔案名稱，當您開啟中的 SharePoint 專案項目時，Visual Studio 編輯器中開啟的檔案**方案總管 中**。 路徑是相對於資料夾，其中包含 *.spdata*檔案。|  
|**FeatureReceiverClass**|選擇性**xs: string**屬性。<br /><br /> 這個 SharePoint 專案項目的功能接收器類別完整的名稱。 如需有關功能接收器的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。|  
|**FeatureReceiverAssembly**|選擇性**xs: string**屬性。<br /><br /> 指定定義此 SharePoint 專案項目的功能接收器的組件完整格式的名稱。 如需有關功能接收器的詳細資訊，請參閱[提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。 如需完整的組件名稱的詳細資訊，請參閱[組件名稱](/dotnet/framework/app-domains/assembly-names)。|  
|**SupportedTrustLevels**|選擇性**xs: string**屬性。<br /><br /> 指定此 SharePoint 專案項目支援的信任層級。 這個值可以是下列字串之一：沙箱化，FullTrust，或全部。 值，所有指定 Sandboxed 和完全信任。<br /><br /> 自訂 SharePoint 專案項目類型中，此屬性的值會對應至值指派給<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>屬性的實作中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 如果您指定不同的值，這個屬性時，Visual Studio 會覆寫值，使它指定您在中指定的相同信任層級<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A>屬性。|  
|**SupportedDeploymentScopes**|選擇性**xs: string**屬性。<br /><br /> 指定此 SharePoint 專案項目支援的部署範圍。 這個值是逗號分隔的字串，其中包含一或多個下列字串：伺服器陣列、 網站、 Web、 WebApplication 或封裝。 例如： `Web, Site`<br /><br /> 自訂 SharePoint 專案項目類型中，此屬性的值會對應至值指派給<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>屬性的實作中<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>方法。 如果您指定不同的值，這個屬性時，Visual Studio 會覆寫值，使它指定您在中指定的相同信任層級<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A>屬性。|  
|**Type**|所需**xs: string**屬性。<br /><br /> SharePoint 專案項目識別碼。 自訂 SharePoint 專案項目類型中，識別碼就是您傳遞給字串<xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>。 如需詳細資訊，請參閱[＜How to：定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。<br /><br /> 如需 Visual Studio 隨附的內建 SharePoint 專案項目識別碼的清單，請參閱[擴充 SharePoint 專案項目](../sharepoint/extending-sharepoint-project-items.md)。|  
  
### <a name="child-elements"></a>子元素
  
|項目|描述|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|選擇性項目。<br /><br /> 代表 SharePoint 專案項目相關聯的自訂資料項目的集合。<br /><br /> 您可以只包含一個**ExtensionData**項目。|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|選擇性項目。<br /><br /> 表示它會部署到 SharePoint 時，會包含與功能的屬性值的集合。<br /><br /> 您可以只包含一個**FeatureProperties**項目。|  
|[檔案](../sharepoint/files-element.md)|選擇性**FileCollectionType**項目。<br /><br /> 指定要部署使用 SharePoint 專案項目，例如功能項目檔和相依的非 SharePoint 專案的輸出檔案。<br /><br /> 加入其中一個**檔案**或是**ProjectItemFolder**項目，但非兩者。|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|選擇性**ProjectItemFolderType**項目。<br /><br /> 表示對應的資料夾。<br /><br /> 加入其中一個**檔案**或是**ProjectItemFolder**項目，但非兩者。|  
|[SafeControls](../sharepoint/safecontrols-element.md)|選擇性項目。<br /><br /> 代表 ASPX 控制項和被指定為安全的任何使用者存取 SharePoint 網站上的任何 ASPX 頁面上的 Web 組件的集合。<br /><br /> 您可以只包含一個**SafeControls**項目。|  
  
### <a name="parent-elements"></a>父元素
 無。  
  
## <a name="element-information"></a>項目資訊
  
|||  
|-|-|  
|**命名空間**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**結構描述名稱**|SharePoint 專案項目結構描述|  
|**驗證檔案**|ProjectItemModelSchema.xsd|  
|**可以是空的**|否|  
  
## <a name="see-also"></a>另請參閱
[SharePoint 專案項目結構描述 rseference](../sharepoint/sharepoint-project-item-schema-reference.md)  
