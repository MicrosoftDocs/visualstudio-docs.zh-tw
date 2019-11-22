---
title: 支援專案和設定屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301071"
---
# <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 整合式開發環境（IDE）中的 [**屬性**] 視窗可以顯示專案和設定屬性。 您可以為自己的專案類型提供屬性頁，讓使用者可以設定應用程式的屬性。  
  
 藉由在**方案總管**中選取專案節點，然後按一下 [**專案**] 功能表上的 [**屬性**]，您就可以開啟包含專案和設定屬性的對話方塊。 在 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 和 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]以及衍生自這些語言的專案類型中，此對話方塊會顯示為 [[一般]、[環境]、[選項] 對話方塊](../../ide/reference/general-environment-options-dialog-box.md)中的索引標籤式頁面。 如需詳細資訊，請參閱[不在組建中：逐步解說：公開專案C#和設定屬性（）](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。  
  
 適用于專案的 Managed 封裝架構（MPFProj）會提供 helper 類別來建立和管理新的專案系統。 您可以在[適用于專案的 MPF](https://archive.codeplex.com/?p=mpfproj12)上找到原始程式碼和編譯指示-Visual Studio 2013。  
  
## <a name="persistence-of-project-and-configuration-properties"></a>專案和設定屬性的持續性  
 專案和設定屬性會保存在副檔名與專案類型相關聯的專案檔中，例如 .csproj、. vbproj 和 myproj.csproj。 語言專案通常會使用範本檔案來產生專案檔案。 不過，實際上有數種方式可讓專案類型和範本產生關聯。 如需詳細資訊，請參閱[筆尖： Visual Studio 範本](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)和[範本目錄描述（）。Vsdir）](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)檔案。  
  
 專案和設定屬性是藉由將專案新增至範本檔案來建立。 然後，使用使用此範本的專案類型所建立的任何專案，都可以使用這些屬性。 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 專案和 MPFProj 都使用[不在組建中：](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde)範本檔案的 MSBuild 總覽架構。 這些檔案具有每個設定的 PropertyGroup 區段。 專案的屬性通常會保存在第一個 PropertyGroup 區段中，其設定引數設為 null 字串。  
  
 下列程式碼顯示基本 MSBuild 專案檔的開頭。  
  
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
  
 在此專案檔中，`<Name>` 和 `<SchemaVersion>` 是專案屬性，而 `<Optimize>` 則是設定屬性。  
  
 專案會負責保存專案檔案的專案和設定屬性。  
  
> [!NOTE]
> 專案可以只保存與預設值不同的屬性值，藉以將持續性優化。  
  
## <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性  
 `Microsoft.VisualStudio.Package.SettingsPage` 類別會執行專案和設定屬性頁。 `SettingsPage` 的預設執行會將公用屬性提供給一般屬性方格中的使用者。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` 方法會從專案屬性方格中選取衍生自 `SettingsPage` 的類別。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` 方法會從設定屬性方格中選取衍生自 `SettingsPage` 的類別。 您的專案類型應該覆寫這些方法，以選取適當的屬性頁。  
  
 `SettingsPage` 類別和 `Microsoft.VisualStudio.Package.ProjectNode` 類別提供下列方法來保存專案和設定屬性：  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 會保存專案屬性。  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 會保存設定屬性。  
  
  > [!NOTE]
  > `Microsoft.VisualStudio.Package.SettingsPage` 和 `Microsoft.VisualStudio.Package.ProjectNode` 類別的執行會使用 `Microsoft.Build.BuildEngine` （MSBuild）方法，從專案檔中取得和設定專案和設定檔案。  
  
  您從 `SettingsPage` 衍生的類別必須執行 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` 和 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties`，才能保存專案檔的專案或設定屬性。  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和登錄路徑  
 衍生自 `SettingsPage` 的類別是設計成可在 Vspackage 間共用。 若要讓 VSPackage 可以建立衍生自 `SettingsPage`的類別，請將 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 新增至衍生自 `Microsoft.VisualStudio.Shell.Package`的類別。  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 附加屬性的 VSPackage 並不重要。 向 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]註冊 VSPackage 時，可以建立的任何物件的類別識別碼（CLSID）都會註冊，以便呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 可以建立它。  
  
 可以建立之物件的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、單字、CLSID 和物件類型的 guid 來決定。 如果 `MyProjectPropertyPage` 類別的 guid 是 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}，而 UserRegistryRoot 是 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp，則登錄路徑會是 HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}。  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>專案和設定屬性屬性和版面配置  
 [<xref:System.ComponentModel.CategoryAttribute>]、[<xref:System.ComponentModel.DisplayNameAttribute>] 和 [<xref:System.ComponentModel.DescriptionAttribute>] 屬性會決定一般屬性頁中的專案和設定屬性的版面配置、標記和描述。 這些屬性會分別決定選項的分類、顯示名稱和描述。  
  
> [!NOTE]
> 對等屬性（SRCategory、LocDisplayName 和 SRDescription）使用字串資源進行當地語系化，並在適用于專案的 MPF 中定義[-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12)。  
  
 請考慮下列程式碼片段：  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 [設定] 屬性頁上的 [`MyConfigProp` 設定] 屬性會顯示為 [我的**類別**] 類別中的 [**我的 Config] 屬性**。 如果選取此選項，[描述] 面板中會出現 [描述]、[**我的描述**]。  
  
## <a name="see-also"></a>另請參閱  
 [不在組建中：逐步解說：公開專案和設定C#屬性（）](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage 狀態](../../misc/vspackage-state.md)   
 [專案](../../extensibility/internals/projects.md)   
 [筆尖： Visual Studio 範本](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
