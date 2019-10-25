---
title: 支援專案和設定屬性 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723164"
---
# <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
@No__t_1 整合式開發環境（IDE）中的 [**屬性**] 視窗可以顯示專案和設定屬性。 您可以為自己的專案類型提供屬性頁，讓使用者可以設定應用程式的屬性。

 藉由在**方案總管**中選取專案節點，然後按一下 [**專案**] 功能表上的 [**屬性**]，您就可以開啟包含專案和設定屬性的對話方塊。 在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 以及衍生自這些語言的專案類型中，此對話方塊會顯示為 [[一般]、[環境]、[選項] 對話方塊](../../ide/reference/general-environment-options-dialog-box.md)中的索引標籤式頁面。 如需詳細資訊，請參閱[不在組建中：逐步解說：公開專案C#和設定屬性（）](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)。

 適用于專案的 Managed 封裝架構（MPFProj）會提供 helper 類別來建立和管理新的專案系統。 您可以在[適用于專案的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)上找到原始程式碼和編譯指示-Visual Studio 2013。

## <a name="persistence-of-project-and-configuration-properties"></a>專案和設定屬性的持續性
 專案和設定屬性會保存在具有任何與專案類型相關聯之副檔名的專案檔中，例如 .csproj、. vbproj 和 myproj.csproj。 語言專案通常會使用範本檔案來產生專案檔案。 不過，實際上有數種方式可讓專案類型和範本產生關聯。 如需詳細資訊，請參閱[範本目錄描述（。Vsdir）](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)檔案。

 專案和設定屬性是藉由將專案新增至範本檔案來建立。 然後，使用使用此範本的專案類型所建立的任何專案，都可以使用這些屬性。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案和 MPFProj 都使用[不在組建中：](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90))範本檔案的 MSBuild 總覽架構。 這些檔案具有每個設定的 PropertyGroup 區段。 專案的屬性通常會保存在第一個 PropertyGroup 區段中，其設定引數設為 null 字串。

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
 @No__t_0 類別會執行專案和設定屬性頁。 @No__t_0 的預設執行會將公用屬性提供給一般屬性方格中的使用者。 @No__t_0 方法會從專案屬性方格中選取衍生自 `SettingsPage` 的類別。 @No__t_0 方法會從設定屬性方格中選取衍生自 `SettingsPage` 的類別。 您的專案類型應該覆寫這些方法，以選取適當的屬性頁。

 @No__t_0 類別和 `Microsoft.VisualStudio.Package.ProjectNode` 類別提供下列方法來保存專案和設定屬性：

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 和 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 會保存專案屬性。

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 和 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 會保存設定屬性。

  > [!NOTE]
  > @No__t_0 和 `Microsoft.VisualStudio.Package.ProjectNode` 類別的執行會使用 `Microsoft.Build.BuildEngine` （MSBuild）方法，從專案檔中取得和設定專案和設定檔案。

  您從 `SettingsPage` 衍生的類別必須執行 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` 和 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties`，才能保存專案檔的專案或設定屬性。

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和登錄路徑
 衍生自 `SettingsPage` 的類別是設計成可在 Vspackage 間共用。 若要讓 VSPackage 可以建立衍生自 `SettingsPage` 的類別，請將 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 新增至衍生自 `Microsoft.VisualStudio.Shell.Package` 的類別。

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 附加屬性的 VSPackage 並不重要。 向 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 註冊 VSPackage 時，可以建立的任何物件的類別識別碼（CLSID）都會註冊，以便呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 可以建立它。

 可以建立之物件的登錄路徑是藉由結合 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、單字、CLSID 和物件類型的 guid 來決定。 如果 `MyProjectPropertyPage` 類別的 guid 為 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}，而 UserRegistryRoot 為 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則登錄路徑會是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0 exp \ CLSID \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}。

## <a name="project-and-configuration-property-attributes-and-layout"></a>專案和設定屬性屬性和版面配置
 [@No__t_0]、[<xref:System.ComponentModel.DisplayNameAttribute>] 和 [<xref:System.ComponentModel.DescriptionAttribute>] 屬性會決定一般屬性頁中的專案和設定屬性的版面配置、標記和描述。 這些屬性會分別決定選項的分類、顯示名稱和描述。

> [!NOTE]
> 對等屬性（SRCategory、LocDisplayName 和 SRDescription）使用字串資源進行當地語系化，並在適用于專案的 MPF 中定義[-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10)。

 請考慮下列程式碼片段：

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 [設定] 屬性頁上的 [`MyConfigProp` 設定] 屬性會顯示為 [我的**類別**] 類別中的 [**我的 Config] 屬性**。 如果選取此選項，[描述] 面板中會出現 [描述]、[**我的描述**]。

## <a name="see-also"></a>請參閱
- [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)
- [專案](../../extensibility/internals/projects.md)
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
