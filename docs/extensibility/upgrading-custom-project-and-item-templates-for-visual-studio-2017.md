---
title: Visual Studio 2017 的升級自訂專案與項目範本
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: d375dfc4a53015f57546f7cbfcc8b940fa81bd0b
ms.sourcegitcommit: 74c5360186731de07828764eb32ea1033a8c2275
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559751"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>升級自訂專案與 Visual Studio 2017 的項目範本

從 Visual Studio 2017 開始，Visual Studio 會探索已安裝的.vsix 或.msi 方式不同於舊版的 Visual Studio 的專案和項目範本。 如果您擁有使用自訂專案或項目範本的延伸模組，您需要更新您的擴充功能。 這篇文章說明您必須。

這項變更會影響僅 Visual Studio 2017。 它不會影響舊版的 Visual Studio。

如果您想要建立專案或項目範本為 VSIX 擴充功能的一部分，請參閱[建立自訂專案與項目範本](../extensibility/creating-custom-project-and-item-templates.md)。

## <a name="template-scanning"></a>掃描的範本

在舊版的 Visual Studio 中， **devenv /setup**或是**devenv /installvstemplates**掃描本機磁碟，若要尋找專案和項目範本。 從 Visual Studio 2017 中，掃描是只能執行使用者層級的位置。 預設使用者層級位置是 **%USERPROFILE%\Documents\\< Visual Studio 版本\>\Templates\\** 。 這個位置用於所產生的範本**專案** > **匯出範本...** 命令時，如果**會自動將範本匯入 Visual Studio**精靈中選取選項。

其他 （非使用者） 的位置，您必須包含指定的位置和範本的其他特性 manifest(.vstman) 檔案。 .Vstman 檔案會產生以及用於範本的.vstemplate 檔案。 如果您安裝您使用.vsix 的延伸模組，您可以完成這需要重新編譯的 Visual Studio 2017 中的擴充功能。 但如果您使用.msi 時，您需要以手動方式進行變更。 如需您要如何進行這些變更的清單，請參閱**升級與安裝的擴充功能。MSI**稍後在此頁面。

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何更新 VSIX 擴充功能專案或項目範本

1. Visual Studio 2017 中開啟的方案。 系統會要求您升級的程式碼。 按一下 [確定]  。

2. 在升級完成之後，您可能需要變更安裝目標版本。 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案中，然後選取**安裝目標**] 索引標籤。如果**版本範圍**欄位是 **[14.0]** ，按一下 [**編輯**並將它變更為包含 Visual Studio 2017。 例如，您可以將它設定為 **[14.0,15.0]** Visual Studio 2015 或 Visual Studio 2017 中，或安裝延伸模組 **[15.0]** 只是 Visual Studio 2017 中安裝它。

3. 重新編譯程式碼。

4. 關閉 Visual Studio。

5. 安裝 VSIX。

6. 您可以透過下列方式來測試更新：

    1. 掃描變更的檔案是由下列登錄機碼啟用：

         **reg 新增 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. 您已新增金鑰之後，請執行**devenv /installvstemplates**。

    3. 重新開啟 Visual Studio。 您應該預期的位置中找到您的範本。

    > [!NOTE]
    > 當登錄機碼存在時，沒有可用的 Visual Studio 擴充性專案範本。 您必須刪除登錄機碼 (和重新執行**devenv /installvstemplates**) 來使用它們。

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>其他建議的部署專案和項目範本

- 請避免使用壓縮的範本檔案。 壓縮檔案必須為未壓縮，以擷取資源和內容的範本，因此它們會來使用。 相反地，您應該部署專案和項目範本，以加速範本初始化自己目錄下的個別檔案。 VSIX 擴充功能，SDK 建置工作會自動將解壓縮壓縮的任何範本建立 VSIX 檔案時。

- 避免在使用範本名稱、 描述、 圖示、 封裝/資源識別碼的項目，或為範本探索期間避免不必要的資源組件載入預覽。 相反地，您可以使用當地語系化的資訊清單來建立每個地區設定使用當地語系化的名稱或屬性的範本項目。

- 如果您要納入做為檔案項目範本，資訊清單產生過程，可能無法提供您預期的結果。 在此情況下，您必須以手動方式產生的資訊清單加入 VSIX 專案。

## <a name="file-changes-in-project-and-item-templates"></a>專案和項目範本中的檔案變更
如此您就可以正確地建立新的檔案，我們會示範 Visual Studio 2015 和 Visual Studio 2017 版本的範本檔案，之間差異的點。

 以下是建立 Visual Studio 2015 的預設專案的.vstemplate 檔案：

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 以下是產生的 VSIX 專案重建.vstman 檔案 （您可以找到它在 VSIX 專案的資訊清單的目錄中）：

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 所提供的資訊[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)項目維持不變。 **\<VSTemplateContainer>** 元素指向相關聯的範本的.vstemplate 檔案。

 以下是 Visual Studio 2015 所建立的預設項目.vstemplate 檔案：

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 以下是產生的 VSIX 專案重建.vstman 檔案 （您可以找到它在 VSIX 專案的資訊清單的目錄中）：

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 所提供的資訊 **\<TemplateData >** 項目維持不變。 **\<VSTemplateContainer>** 元素指向相關聯的範本的.vstemplate 檔案

 如需有關.vstman 檔案的不同元素的詳細資訊，請參閱[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>安裝擴充功能的升級。MSI

有些以 MSI 為基礎的延伸模組會將範本部署到一般的範本位置，例如下列目錄：

- **\<Visual Studio 安裝目錄 > \Common7\IDE\\< ProjectTemplates/項目範本\>**

- **\<Visual Studio 安裝目錄 > \Common7\IDE\Extensions\\< ExtensionName\>\\< 專案/項目範本\>**

如果您的延伸模組執行 MSI 為基礎的部署，您需要手動產生範本資訊清單，並確保它包含延伸模組安裝程式中。 比較上述.vstman 範例和[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

建立專案和項目範本的不同資訊清單，並應指向根範本指定目錄上方。 建立每個延伸模組和地區設定的一份資訊清單。

## <a name="see-also"></a>另請參閱

- [範本探索進行疑難排解](troubleshooting-template-discovery.md)
- [建立自訂專案和項目範本](creating-custom-project-and-item-templates.md)
