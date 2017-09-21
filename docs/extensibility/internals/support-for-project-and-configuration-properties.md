---
title: "專案和組態屬性的支援 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案屬性中，以 Visual Studio SDK 支援"
  - "組態屬性，Visual Studio sdk suppporting"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 專案和組態屬性的支援
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**屬性** \] 視窗中的 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式的開發環境 \(IDE\) 可顯示專案和設定屬性。 使用者可設定您的應用程式的屬性，您可以提供您自己的專案類型屬性頁。  
  
 藉由選取的專案節點中 **方案總管\] 中** ，然後按一下 \[ **屬性** 上 **專案** \] 功能表上，您可以開啟一個對話方塊，包括專案和組態屬性。 在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], ，和專案類型衍生自這些語言的這個對話方塊會出現在索引標籤式頁面 [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)。 如需詳細資訊，請參閱 [不在建置︰ 逐步解說︰ 公開的專案和設定屬性 \(C\#\)](http://msdn.microsoft.com/zh-tw/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。  
  
 管理封裝個專案的架構 \(MPFProj\) 提供建立和管理新的專案系統的協助程式類別。 您可以在程式碼並編譯指示找出來源 [專案\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
## 專案範本和組態屬性的持續性  
 專案和組態屬性會保存在與專案類型，例如相關聯的檔案副檔名、.csproj、.vbproj 和.myproj 的專案檔案。 語言專案通常會使用範本檔案來產生專案檔。 不過，有很多種實際專案類型和範本建立關聯。 如需詳細資訊，請參閱 [NIB: Visual Studio 範本](http://msdn.microsoft.com/zh-tw/141fccaa-d68f-4155-822b-27f35dd94041) 和 [範本目錄描述 \(。Vsdir\) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
 將項目加入到範本檔案會建立專案和組態屬性。 這些屬性可使用的專案類型，會使用此範本所建立的任何專案。[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案和兩者都使用 MPFProj [不在建置︰ MSBuild 概觀](http://msdn.microsoft.com/zh-tw/b588fd73-a45b-4706-908f-cc131bccfbde) 範本檔案的結構描述。 這些檔案都有每個組態的 PropertyGroup 區段。 專案的屬性通常會保存在第一個的 PropertyGroup 區段具有組態引數設定為 null 字串。  
  
 下列程式碼示範基本的 MSBuild 專案檔的開頭。  
  
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
  
 在專案檔案中， `<Name>` 和 `<SchemaVersion>` 專案屬性和 `<Optimize>` 為組態屬性。  
  
 它負責保存專案和設定屬性的專案檔案的專案。  
  
> [!NOTE]
>  專案可以最佳化持續性保存其預設值不同的唯一屬性值。  
  
## 專案和組態屬性的支援  
 `Microsoft.VisualStudio.Package.SettingsPage` 類別會實作專案\] 和 \[組態屬性頁。 預設實作 `SettingsPage` 泛型屬性方格中的使用者提供的公用屬性。`Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` 方法會選取衍生自類別 `SettingsPage` 專案屬性方格。`Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` 方法會選取衍生自類別 `SettingsPage` 的組態屬性方格。 您的專案類型應該覆寫這些方法來選取適當的屬性頁。  
  
 `SettingsPage` 類別和 `Microsoft.VisualStudio.Package.ProjectNode` 類別會提供這些方法來保存專案和組態屬性︰  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 保存專案屬性。  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 保存組態屬性。  
  
    > [!NOTE]
    >  實作 `Microsoft.VisualStudio.Package.SettingsPage` 和 `Microsoft.VisualStudio.Package.ProjectNode` 類別會使用 `Microsoft.Build.BuildEngine` \(MSBuild\) 方法來取得及設定專案和組態屬性，從專案檔。  
  
 此類別衍生自 `SettingsPage` 必須實作 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` 和 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 保存專案或組態的專案檔的內容。  
  
## ProvideObjectAttribute 以及登錄路徑  
 類別衍生自 `SettingsPage` 專為 VSPackages 之間共用。 若要使建立衍生自類別 VSPackage `SettingsPage`, ，加入 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 類別衍生自 `Microsoft.VisualStudio.Shell.Package`。  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 VSPackage 要附加屬性並不重要。 VSPackage 向時 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ，您可以建立任何物件的類別識別碼 \(CLSID\) 登錄，讓呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 可以建立。  
  
 您可以建立物件的登錄路徑由合併 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, ，word、 CLSID、 和物件類型的 guid。 如果 `MyProjectPropertyPage` 類別具有 {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} 的 guid 和 UserRegistryRoot 是 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp，則登錄路徑會是 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}。  
  
## 專案和設定屬性的屬性和配置。  
 <xref:System.ComponentModel.CategoryAttribute>, ，<xref:System.ComponentModel.DisplayNameAttribute>, ，和 <xref:System.ComponentModel.DescriptionAttribute> 屬性會決定配置、 標記、 和一般屬性頁面中的專案和設定屬性的描述。 這些屬性決定的類別，分別顯示名稱和選項的描述。  
  
> [!NOTE]
>  對等的屬性、 SRCategory、 LocDisplayName 和 SRDescription，用於當地語系化字串資源，且已定義在 [專案\-Visual Studio 2013 的 MPF](http://mpfproj12.codeplex.com/)。  
  
 請考慮下列程式碼片段：  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` 組態屬性會出現在組態屬性\] 頁面上，做為 **我的組態屬性** 在類別中， **My Category**。 如果選取此選項，則描述 **我描述**, ，會出現在 \[描述\] 面板。  
  
## 請參閱  
 [不在建置︰ 逐步解說︰ 公開專案和組態屬性 \(C\#\)](http://msdn.microsoft.com/zh-tw/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [加入和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage 狀態](/visual-cpp/misc/vspackage-state)   
 [專案](../../extensibility/internals/projects.md)   
 [NIB：Visual Studio 範本](http://msdn.microsoft.com/zh-tw/141fccaa-d68f-4155-822b-27f35dd94041)   
 [範本目錄描述 \(。Vsdir\) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)