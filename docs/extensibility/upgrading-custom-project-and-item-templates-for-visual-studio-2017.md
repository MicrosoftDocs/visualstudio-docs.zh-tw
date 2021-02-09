---
title: 升級 Visual Studio 2017 的自訂專案和專案範本
titleSuffix: ''
description: 瞭解如何從舊版 Visual Studio SDK 更新您的自訂專案和專案範本，以搭配 Visual Studio 2017 和更新版本使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 84e9b08350cf5977269bfbcf28ca5335e17f024d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893401"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>升級自訂 Visual Studio 的專案與項目範本2017

從 Visual Studio 2017 開始，Visual Studio 會探索由 .vsix 或 .msi 以不同方式安裝在舊版 Visual Studio 的專案和專案範本。 如果您擁有使用自訂專案或專案範本的擴充功能，則必須更新您的延伸模組。 本文說明您必須做的事。

此變更只會影響 Visual Studio 2017。 它不會影響舊版 Visual Studio。

如果您想要建立專案或專案範本作為 VSIX 擴充功能的一部分，請參閱 [建立自訂專案和專案範本](../extensibility/creating-custom-project-and-item-templates.md)。

## <a name="template-scanning"></a>範本掃描

在舊版 Visual Studio 中， **devenv/setup** 或 **devenv/installvstemplates** 掃描本機磁片以尋找專案和專案範本。 從 Visual Studio 2017 開始，掃描只會針對使用者層級位置執行。 預設的使用者層級位置是 **%USERPROFILE%\Documents \\<Visual Studio 版本 \> \Templates \\**。   >  如果已在 wizard 中選取 [**自動將範本匯入 Visual Studio** ] 選項，則會使用這個位置作為 [專案 **匯出範本**] 命令所產生的範本。

針對其他 (非使用者) 位置，您必須包含指定範本位置和其他特性的資訊清單 (. vstman) 檔。 Vstman 檔案會連同用於範本的 .vstemplate 檔案一起產生。 如果您使用 .vsix 安裝您的延伸模組，您可以在 Visual Studio 2017 中重新編譯延伸模組來完成這項操作。 但是，如果您使用 .msi，則需要手動進行變更。 如需進行這些變更所需執行的動作清單，請參閱  **隨安裝的擴充功能更新。** 此頁面稍後的 MSI。

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何使用專案或專案範本更新 VSIX 擴充功能

1. 在 Visual Studio 2017 中開啟方案。 系統會要求您升級程式碼。 按一下 [確定]  。

2. 升級完成之後，您可能需要變更安裝目標的版本。 在 VSIX 專案中，開啟 extension.vsixmanifest 檔案，然後選取 [ **安裝目標** ] 索引標籤。如果 [ **版本範圍** ] 欄位是 **[14.0]**，請按一下 [ **編輯** ]，並將其變更為包含 Visual Studio 2017。 例如，您可以將它設定為 **[14.0，15.0]** 以將延伸模組安裝到 Visual Studio 2015 或 Visual Studio 2017，或 **[15.0]** 將它安裝到只 Visual Studio 2017。

3. 重新編譯程式碼。

4. 關閉 Visual Studio。

5. 安裝 VSIX。

6. 您可以執行下列動作來測試更新：

    1. 檔案掃描變更會由下列登錄機碼啟用：

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg：32**

    2. 新增金鑰之後，請執行 **devenv/installvstemplates**。

    3. 重新開啟 Visual Studio。 您應該會在預期的位置找到您的範本。

    > [!NOTE]
    > 當登錄機碼存在時，就無法使用 Visual Studio 擴充性專案範本。 您必須刪除登錄機碼 (然後重新執行 **devenv/installvstemplates**) ，才能使用它們。

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>部署專案和專案範本的其他建議

- 避免使用壓縮的範本檔案。 壓縮的範本檔案需要解壓縮才能取得資源和內容，因此將會越大使用。 相反地，您應該將專案和專案範本以個別檔案的形式部署至自己的目錄，以加快範本初始化的速度。 針對 VSIX 擴充功能，SDK 組建工作會在建立 VSIX 檔案時自動解壓縮任何壓縮的範本。

- 請避免使用套件/資源識別碼專案作為範本名稱、描述、圖示或預覽，以避免在範本探索期間載入不必要的資源元件。 相反地，您可以使用當地語系化的資訊清單來建立每個地區設定的範本專案，而該專案會使用當地語系化的名稱或屬性。

- 如果您以檔案專案的形式包含範本，則資訊清單產生可能無法提供預期的結果。 在這種情況下，您必須將手動產生的資訊清單新增至 VSIX 專案。

## <a name="file-changes-in-project-and-item-templates"></a>專案和專案範本中的檔案變更
我們會顯示 Visual Studio 2015 與 Visual Studio 2017 版本的範本檔案之間的差異點，讓您可以正確地建立新的檔案。

 以下是 Visual Studio 2015 所建立的預設專案 .vstemplate 檔案：

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

 以下是 vstman 檔案 (您可以在 VSIX 專案的資訊清單目錄) （因為重建 VSIX 專案所產生）中找到它：

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

 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)元素所提供的資訊維持不變。 **\<VSTemplateContainer>** 元素指向關聯範本的 .vstemplate 檔案。

 以下是 Visual Studio 2015 所建立的預設專案 .vstemplate 檔案：

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

 以下是 vstman 檔案 (您可以在 VSIX 專案的資訊清單目錄) （因為重建 VSIX 專案所產生）中找到它：

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

 元素所提供的資訊會保持不變 **\<TemplateData>** 。 **\<VSTemplateContainer>** 元素指向關聯範本的 .vstemplate 檔案。

 如需 vstman 檔案的不同元素的詳細資訊，請參閱 [Visual Studio 範本資訊清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>升級與一起安裝的擴充功能。微星

某些以 MSI 為基礎的擴充功能會將範本部署至一般範本位置，例如下列目錄：

- **\<Visual Studio installation directory>\Common7\IDE \\<>\templates\projecttemplates\csharp\helloworld\/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<Project/ItemTemplates\>**

如果您的延伸模組會執行以 MSI 為基礎的部署，您需要手動產生範本資訊清單，並確定它包含在延伸模組設定中。 比較上面所列的 vstman 範例和 [Visual Studio 範本資訊清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

為專案和專案範本建立個別的資訊清單，它們應該指向上述所指定的根範本目錄。 為每個延伸模組和地區設定建立一個資訊清單。

## <a name="see-also"></a>另請參閱

- [針對範本探索進行疑難排解](troubleshooting-template-discovery.md)
- [建立自訂專案和專案範本](creating-custom-project-and-item-templates.md)
