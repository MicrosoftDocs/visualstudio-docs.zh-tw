---
title: 專案和設定屬性的支援 |Microsoft Docs
description: 瞭解如何在 Visual Studio IDE 中為您自己的專案類型提供屬性頁，以便顯示專案和設定擴充屬性。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd5f15f16894faf6d47700e34db4d99a1fa3cb5a
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876593"
---
# <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
整合式開發環境 (IDE) 中的 [ **屬性** ] 視窗 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 可以顯示專案和設定屬性。 您可以為自己的專案類型提供屬性頁，讓使用者可以設定應用程式的屬性。

 藉由在 **方案總管** 中選取專案節點，然後按一下 [**專案**] 功能表上的 [**屬性**]，您可以開啟包含專案和設定屬性的對話方塊。 在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 和中， [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 以及從這些語言衍生的專案類型，此對話方塊會在 [ [一般]、[環境]、[選項] 對話方塊](../../ide/reference/general-environment-options-dialog-box.md)中顯示為索引標籤式頁面。 如需詳細資訊，請參閱 [不在組建中：逐步解說：公開專案和設定屬性 (c # ) ](/previous-versions/bb166517(v=vs.100))。

 適用于專案的 Managed 封裝架構 (MPFProj) 提供協助程式類別來建立和管理新的專案系統。 您可以在 [適用于專案的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)上找到原始程式碼和編譯指示-Visual Studio 2013。

## <a name="persistence-of-project-and-configuration-properties"></a>專案和設定屬性的持續性
 專案和設定屬性會保存在專案檔中，該專案檔具有任何與專案類型相關聯的副檔名，例如 .csproj、. vbproj 和. myproj.csproj。 語言專案通常會使用範本檔案來產生專案檔。 不過，實際上有幾種方式可以建立專案類型和範本的關聯性。 如需詳細資訊，請參閱 [範本目錄描述 (。Vsdir) ](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)檔。

 專案和設定屬性是藉由將專案新增至範本檔案來建立。 然後，這些屬性可用於使用此範本的專案類型所建立的任何專案。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案和 MPFProj 都使用 [Not In Build：](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) 範本檔案的 MSBuild 總覽架構。 這些檔案的每個設定都有一個 PropertyGroup 區段。 專案的屬性通常會保存在第一個 PropertyGroup 區段，其設定引數設定為 null 字串。

 下列程式碼顯示基本 MSBuild 專案檔案的開頭。

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

 在這個專案檔中， `<Name>` 和 `<SchemaVersion>` 是專案屬性，而且 `<Optimize>` 是設定屬性。

 專案必須負責保存專案檔的專案和設定屬性。

> [!NOTE]
> 專案可以只保存與預設值不同的屬性值，以優化持續性。

## <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
 類別會執行 `Microsoft.VisualStudio.Package.SettingsPage` 專案和設定屬性頁。 的預設實作為 `SettingsPage` 泛型屬性方格中的使用者提供公用屬性。 `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`方法會從專案屬性方格選取衍生自 `SettingsPage` 的類別。 `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`方法會針對設定屬性方格選取衍生自的類別 `SettingsPage` 。 您的專案類型應覆寫這些方法，以選取適當的屬性頁。

 `SettingsPage`類別和 `Microsoft.VisualStudio.Package.ProjectNode` 類別提供這些方法來保存專案和設定屬性：

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` 並 `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` 保存專案屬性。

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` 並 `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` 保存設定屬性。

  > [!NOTE]
  > 和類別的實 `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` 使用 `Microsoft.Build.BuildEngine` (MSBuild) 方法，從專案檔取得和設定專案和設定屬性。

  您衍生自的類別 `SettingsPage` 必須執行 `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` ，並保存專案檔的 `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` 專案或設定屬性。

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute 和登錄路徑
 衍生自 `SettingsPage` 的類別是設計來跨 vspackage 共用。 若要讓 VSPackage 可以建立衍生自的類別 `SettingsPage` ，請將加入 `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` 至衍生自的類別 `Microsoft.VisualStudio.Shell.Package` 。

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 附加屬性的 VSPackage 並不重要。 當註冊 VSPackage 時，會 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 註冊可建立之任何物件的類別識別碼 (CLSID) ，以便呼叫來 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> 建立它。

 可以建立之物件的登錄路徑是透過合併 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> 、單字、CLSID 以及物件類型的 guid 來決定。 如果 `MyProjectPropertyPage` 類別的 guid 為 {3c693da2-5bca-49b3-bd95-ffe0a39dd723}，而 UserRegistryRoot 為 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp，則登錄路徑會是 HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\CLSID\\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}。

## <a name="project-and-configuration-property-attributes-and-layout"></a>專案和設定屬性屬性和版面配置
 <xref:System.ComponentModel.CategoryAttribute>、 <xref:System.ComponentModel.DisplayNameAttribute> 和屬性會 <xref:System.ComponentModel.DescriptionAttribute> 決定一般屬性頁中專案和設定屬性的版面配置、標記和描述。 這些屬性會分別決定選項的類別、顯示名稱和描述。

> [!NOTE]
> 對等的屬性（SRCategory、LocDisplayName 和 SRDescription）會使用字串資源進行當地語系化，並在 [適用于專案 Visual Studio 2013 的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)中定義。

 請考慮下列程式碼片段：

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 設定屬性會在 [設定] 屬性 `MyConfigProp` 頁上顯示為 [**我** 的分類] 類別中的 [我的設定]**屬性**。 如果選取此選項，[描述]、[ **我的描述**] 會出現在 [描述] 面板中。

## <a name="see-also"></a>請參閱
- [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)
- [專案](../../extensibility/internals/projects.md)
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)