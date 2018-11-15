---
title: 支援專案和組態屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 783c73cc73da188ec1be626cf54db93ca62af465
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865098"
---
# <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
**屬性** 視窗中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 可以顯示專案和設定的屬性。 使用者可設定您的應用程式的屬性，您可以將屬性頁提供您自己的專案類型中。  
  
 藉由選取中的專案節點**方案總管**，然後按一下**屬性**上**專案** 功能表中，您可以開啟包含專案和設定的對話方塊屬性。 在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]並[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]，和專案類型衍生自這些語言的索引標籤式頁面中會出現此對話方塊[一般、 環境、 選項對話方塊](../../ide/reference/general-environment-options-dialog-box.md)。 如需詳細資訊，請參閱 <<c0> [ 不在組建中： 逐步解說： 公開專案和組態屬性 (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。  
  
 Managed Package Framework 中的專案 (MPFProj) 提供用於建立和管理新的專案系統的協助程式類別。 您可以找到來源的程式碼和編譯指示[專案-Visual Studio 2013 的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)。  
  
## <a name="persistence-of-project-and-configuration-properties"></a>持續性的專案和組態屬性  
 專案和設定的屬性會保存在專案檔具有任何副檔名與專案類型關聯，例如、.csproj、.vbproj、 和.myproj。 語言專案通常會使用範本檔案來產生專案檔。 不過，有很多種實際專案類型和範本建立關聯。 如需詳細資訊，請參閱[範本目錄描述 (。Vsdir) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
 將項目加入至範本檔案會建立專案和設定的屬性。 這些屬性便可使用的專案類型，會使用此範本建立的任何專案。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案和兩者都使用 MPFProj[不在組建中： MSBuild 概觀](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90))範本檔案的結構描述。 這些檔案都有每個組態的 PropertyGroup 區段。 專案的屬性通常會保存在第一次的 PropertyGroup 區段有組態引數設定為 null 的字串。  
  
 下列程式碼會顯示基本的 MSBuild 專案檔的開頭。  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 在此專案檔中，`<Name>`並`<SchemaVersion>`專案屬性和`<Optimize>`為組態屬性。  
  
 負責的專案，以保存專案和設定屬性的專案檔。  
  
> [!NOTE]
>  專案可以最佳化持續性保存其預設值不同的唯一屬性值。  
  
## <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性  
 `Microsoft.VisualStudio.Package.SettingsPage`類別會實作專案] 和 [組態屬性頁。 預設實作`SettingsPage`泛型屬性方格中的使用者提供的公用屬性。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`方法會選取類別衍生自`SettingsPage`的專案屬性方格。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`方法會選取類別衍生自`SettingsPage`的組態屬性方格。 您的專案類型應該覆寫這些方法來選取適當的屬性頁面。  
  
 `SettingsPage`類別和`Microsoft.VisualStudio.Package.ProjectNode`類別會提供這些方法來保存專案和設定的屬性：  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和`Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`保存專案屬性。  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和`Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`保存組態屬性。  
  
  > [!NOTE]
  >  實作`Microsoft.VisualStudio.Package.SettingsPage`並`Microsoft.VisualStudio.Package.ProjectNode`類別會使用`Microsoft.Build.BuildEngine`(MSBuild) 方法來取得和設定從專案檔的專案] 和 [組態屬性。  
  
  此類別衍生自`SettingsPage`必須實作`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`和`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`以保留的專案檔的專案] 或 [組態屬性。  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和登錄路徑  
 類別衍生自`SettingsPage`專為在 Vspackage 之間共用。 若要可讓 VSPackage 也可以建立一個衍生自類別`SettingsPage`，新增`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`類別，衍生自`Microsoft.VisualStudio.Shell.Package`。  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 要附加屬性的 VSPackage 並不重要。 當 VSPackage 註冊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，類別識別碼 (CLSID)，您可以建立任何物件的已註冊，讓呼叫<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>可以建立它。  
  
 物件，您可以建立的登錄路徑由合併<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>，word、 CLSID、 和物件類型的 guid。 如果`MyProjectPropertyPage`類別具有 {3c693da2-5bca-49b3-bd95-ffe0a39dd723} 的 guid 和 UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則會 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio 登錄路徑。\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>專案和組態屬性的屬性和配置。  
 <xref:System.ComponentModel.CategoryAttribute>， <xref:System.ComponentModel.DisplayNameAttribute>，和<xref:System.ComponentModel.DescriptionAttribute>屬性會決定配置、 標記和一般屬性頁面中的專案和設定屬性的描述。 這些屬性決定的類別，分別顯示名稱和描述的選項。  
  
> [!NOTE]
>  對等的屬性、 SRCategory、 LocDisplayName，SRDescription，字串資源當地語系化，並使用定義於[專案-Visual Studio 2013 的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)。  
  
 請考慮下列程式碼片段：  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp`組態屬性會出現在 [組態] 屬性頁面，為**我的組態屬性**在類別中， **My Category**。 如果選取此選項，則描述**我描述**，會出現在 [描述] 面板。  
  
## <a name="see-also"></a>另請參閱  
 [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)   
 [專案](../../extensibility/internals/projects.md)   
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
