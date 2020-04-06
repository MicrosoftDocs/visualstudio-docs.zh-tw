---
title: 升級 Visual Studio 2017 的自訂項目和專案範本
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698851"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>升級視覺化工作室 2017 的自訂項目和專案範本

從 Visual Studio 2017 開始,Visual Studio 會發現由 .vsix 或 .msi 以不同於早期版本的 Visual Studio 安裝的專案和專案範本。 如果您擁有使用自定義專案或專案範本的擴展,則需要更新擴展。 本文介紹了您必須做什麼。

此更改僅影響 Visual Studio 2017。 它不會影響早期版本的 Visual Studio。

如果要建立項目或專案樣本作為 VSIX 延伸的一部分,請參閱[建立自訂項目和專案樣本](../extensibility/creating-custom-project-and-item-templates.md)。

## <a name="template-scanning"></a>樣本掃描

在 Visual Studio 的早期版本中 **,devenv /安裝程式**或**devenv /installvstemplate**掃描本地磁碟以查找專案和專案範本。 從 Visual Studio 2017 開始,掃描僅針對使用者級位置執行。 預設使用者級位置是 **%USERPROFILE%%\\\文件\><可视化工作室版本 \Templates\\**。 如果嚮導中選擇了 **「自動將範本導入 Visual Studio」** 選項,則此位置用於由**專案** > **匯出範本..."** 命令生成的範本。

對於其他(非使用者)位置,必須包含一個清單(.vstman)檔,該檔指定範本的位置和其他特徵。 .vstman 檔與用於範本的 .vstemplate 檔案一起生成。 如果使用 .vsix 安裝擴展,則可以通過在 Visual Studio 2017 中重新編譯擴展來實現此目的。 但是,如果您使用 .msi,則需要手動進行更改。 有關進行這些更改需要執行哪些操作的清單,請參閱使用 安裝的**擴展的升級。MSI**稍後在本頁。

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何使用項目或專案樣本更新 VSIX 延伸

1. 在 Visual Studio 2017 中打開解決方案。 系統將要求您升級代碼。 按一下 [確定]  。

2. 升級完成後,您可能需要更改安裝目標的版本。 在 VSIX 專案中,開啟來源.擴展.vsixmanifest 檔案並選擇「**安裝目標**」選項卡。如果**版本範圍「** 欄位為 **[14.0],** 請按下 **「編輯」** 並將其更改為包括 Visual Studio 2017。 例如,您可以將其設置為 **{14.0,15.0}** 以將擴展安裝到 Visual Studio 2015 或 Visual Studio 2017,或者將其設置為 **[15.0]** 以將其安裝到 Visual Studio 2017。

3. 重新編譯代碼。

4. 關閉 Visual Studio。

5. 安裝 VSIX。

6. 您可以透過執行以下操作來測試更新:

    1. 檔案掃描變更由以下註冊表項啟動:

         **reg 新增 hklm_software_microsoft_visualstudio_15.0_VSTemplate /v 禁用範本掃描 /t REG_DWORD /d 1 /reg:32**

    2. 添加金鑰後,執行**devenv /installvstemplate。**

    3. 重新打開視覺工作室。 您應該在預期位置找到範本。

    > [!NOTE]
    > 當註冊表項存在時,Visual Studio 擴充性專案範本不可用。 您必須刪除註冊表項(並重新執行**devenv /installvstemplate)** 才能使用它們。

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>部署項目與項目樣本的其他建議

- 避免使用壓縮範本檔。 壓縮範本檔需要取消壓縮才能檢索資源和內容,因此它們使用成本更高。 相反,應將專案和專案範本部署為其目錄下的單個檔,以加快範本初始化。 對於 VSIX 擴展,SDK 生成任務將在創建 VSIX 檔時自動解壓縮任何壓縮範本。

- 避免對範本名稱、說明、圖示或預覽使用包/資源 ID 條目,以避免在範本發現期間載入不必要的資源程式集。 相反,您可以使用當地語系化的清單為每個區域設置創建範本項目,該區域設置使用當地語系化的名稱或屬性。

- 如果將範本作為檔項包含,則清單生成可能不會為您提供預期的結果。 在這種情況下,您必須向 VSIX 專案添加手動生成的清單。

## <a name="file-changes-in-project-and-item-templates"></a>專案與專案樣本的檔案變更
我們顯示 Visual Studio 2015 和 Visual Studio 2017 版本的範本檔之間的差異點,以便您可以正確創建新檔。

 下面是 Visual Studio 2015 建立的預設專案 .vstemplate 檔案:

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

 下面是由重建 VSIX 項目產生的 .vstman 檔案(您可以在 VSIX 專案的清單目錄中找到它):

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

 [範本資料](../extensibility/templatedata-element-visual-studio-templates.md)元素提供的資訊保持不變。 VSTemplate 容器>元素指向關聯範本的 .vstemplate**\<** 檔案。

 下面是 Visual Studio 2015 建立的預設項 .vstemplate 檔案:

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

 下面是由重建 VSIX 項目產生的 .vstman 檔案(您可以在 VSIX 專案的清單目錄中找到它):

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

 範本資料>元素提供的資訊保持不變。 ** \< ** VSTemplate 容器>元素指向關聯範本的 .vstemplate 檔案**\<**

 有關 .vstman 檔案的不同元素的詳細資訊,請參閱[可視化工作室範本清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>使用安裝的擴展的升級。微星

某些基於 MSI 的延伸將樣本部署到常見的樣本位置,例如以下目錄:

- **\<可視化工作室安裝目錄>_通用7_IDE<\\專案範本/專案範本\>**

- **\<可視化工作室安裝目錄>_Common7_IDE_擴展\\\>\\<扩展名称<项目/專案範本\>**

如果擴展執行基於 MSI 的部署,則需要手動生成範本清單,並確保範本包含在擴展設置中。 比較上面列出的 .vstman 範例與[視覺化工作室樣本清單架構參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

為專案和專案範本創建單獨的清單,它們應指向上面指定的根範本目錄。 每個擴展和區域設置創建一個清單。

## <a name="see-also"></a>另請參閱

- [容錯排除範本發現](troubleshooting-template-discovery.md)
- [建立自訂項目與專案樣本](creating-custom-project-and-item-templates.md)
