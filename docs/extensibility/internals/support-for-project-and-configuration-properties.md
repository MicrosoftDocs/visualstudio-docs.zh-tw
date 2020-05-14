---
title: 對專案和設定屬性的支援 |微軟文件
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
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704893"
---
# <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
整合式開發環境 (IDE) 中的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**「屬性**」 視窗可以顯示專案和設定屬性。 您可以為自己的項目類型提供屬性頁,以便使用者可以為應用程式設置屬性。

 通過在**解決方案資源管理器**中選擇專案節點,然後單擊 **「專案**」功能表上**的屬性**,可以打開包含專案和配置屬性的對話框。 在[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)][!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和和派生自這些語言的項目類型中,此對話框在[「常規、環境、選項」對話框](../../ide/reference/general-environment-options-dialog-box.md)中顯示為選項卡式頁面。 有關詳細資訊,請參閱[不在生成中:演練:公開專案和配置屬性 (C#)。](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)

 專案管理套件框架 (MPFProj) 提供用於創建和管理新專案系統的幫助程式類。 您可以在[專案 MPF - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10)找到原始碼和編譯說明。

## <a name="persistence-of-project-and-configuration-properties"></a>專案與設定屬性的持久性
 專案和設定屬性將保留在具有與專案類型關聯的任何檔名副檔名的專案檔中,例如 .csproj、.vbproj 和 .myproj。 語言專案通常使用範本檔生成專案檔。 但是,實際上有幾種方法可以關聯項目類型和範本。 有關詳細資訊,請參閱[範本目錄說明 (。Vsdir 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。

 專案和配置屬性是透過向樣本檔添加項來創建的。 然後,這些屬性可用於使用使用此範本的項目類型創建的任何專案。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案和 MPFProj 都使用[樣本檔的「不在生成中:MS構建概述](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90))」架構。 這些檔具有每個配置的屬性組部分。 專案的屬性通常保留在第一屬性組部分,該部分具有設置為空字串的配置參數。

 以下代碼顯示基本 MSBuild 專案檔的開始。

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

 在此項目檔中,`<Name>``<SchemaVersion>`並且是專案屬性,`<Optimize>`並且是配置屬性。

 專案負責保留專案檔的專案和配置屬性。

> [!NOTE]
> 專案可以通過僅保留與其預設值不同的屬性值來優化持久性。

## <a name="support-for-project-and-configuration-properties"></a>支援專案和組態屬性
 類`Microsoft.VisualStudio.Package.SettingsPage`實現專案和配置屬性頁。 預設`SettingsPage`實現向泛型屬性網格中的使用者提供公共屬性。 該方法`Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`選擇派生`SettingsPage`自 項目屬性網格的類。 該方法`Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`選擇派生`SettingsPage`自 配置屬性網格的類。 項目類型應重寫這些方法以選擇適當的屬性頁。

 類別`SettingsPage`與`Microsoft.VisualStudio.Package.ProjectNode`類別提供以下方法來保留專案與設定屬性:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`並`Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty`保留專案屬性。

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`並`Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty`保留配置屬性。

  > [!NOTE]
  > 和類的實現使用`Microsoft.Build.BuildEngine`(MSBuild) 方法從專案檔中獲取和設置專案和配置`Microsoft.VisualStudio.Package.ProjectNode``Microsoft.VisualStudio.Package.SettingsPage`屬性。

  派生自`SettingsPage`的類必須`Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges`實現`Microsoft.VisualStudio.Package.SettingsPage.BindProperties`並保留專案檔的專案或配置屬性。

## <a name="provideobjectattribute-and-registry-path"></a>提供物件屬性和註冊表路徑
 派生的`SettingsPage`類設計為跨 VSPackages 共用。 為了使 VSPackage 能夠建立派生`SettingsPage`自 的 類`Microsoft.VisualStudio.Shell.ProvideObjectAttribute`,請將 a`Microsoft.VisualStudio.Shell.Package`添加到派生自 的類。

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 附加到該屬性的 VS 包並不重要。 當 VSPackage[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊時 ,將註冊任何可創建物件的類 ID (CLSID),以便調用 可以<xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A>創建它。

 可以創建的物件的註冊錶路徑通過組合<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、單詞、CLSID和物件類型的guid來確定。 如果`MyProjectPropertyPage`類的 guid 為 {3c693da2-5bca-49b3-bd95-ffe0a39d723},並且使用者註冊Root 是HKEY_CURRENT_USER\軟體\微軟_VisualStudio_8.0Exp, 然後註冊錶路徑將是HKEY_CURRENT_USER\\\軟體\微軟_VisualStudio_8.0Exp_CLSID {3c693da2-5bca-49b3-bd95-ffe0a39d723}。

## <a name="project-and-configuration-property-attributes-and-layout"></a>專案與設定屬性屬性和佈局
 <xref:System.ComponentModel.DisplayNameAttribute>和<xref:System.ComponentModel.CategoryAttribute>屬性確定泛型屬性頁中的專案和配置屬性的佈局、標<xref:System.ComponentModel.DescriptionAttribute>記和說明。 這些屬性分別確定選項的類別、顯示名稱和說明。

> [!NOTE]
> 等效屬性、SR 類別、LocDisplayName 和 SR 描述,使用字串資源進行當地語系化,並在[專案 MPF 中定義 - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10)。

 請考慮下列程式碼片段：

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 設定`MyConfigProp`屬性在設定屬性頁上顯示為類別中**的"我的****設定**屬性" 如果選擇了該選項,則說明"**我的描述**"將顯示在說明面板中。

## <a name="see-also"></a>另請參閱
- [新增和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)
- [專案](../../extensibility/internals/projects.md)
- [範本目錄描述檔 (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
