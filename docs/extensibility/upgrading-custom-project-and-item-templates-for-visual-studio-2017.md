---
title: 升級自訂專案與 Visual Studio 2017 的項目範本 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af60281e7211e7b16e86200c02aef791d26da274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143474"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>升級自訂專案與 Visual Studio 2017 的項目範本

從 Visual Studio 2017 開始，Visual Studio 會探索已由.vsix 或.msi 安裝在不同的方式與舊版 Visual Studio 中的專案和項目範本。 如果您擁有使用自訂專案或項目範本的擴充功能，您需要更新您的擴充功能。 本主題說明您必須。

這項變更會影響只有 Visual Studio 2017。 它不會影響舊版的 Visual Studio。

如果您想要建立專案或項目範本為 VSIX 擴充功能的一部分，請參閱[建立自訂專案與項目範本](../extensibility/creating-custom-project-and-item-templates.md)。

## <a name="template-scanning"></a>掃描的範本

在舊版的 Visual Studio 中， **devenv /setup**或**devenv /installvstemplates**掃描本機的磁碟，以便尋找專案和項目範本。 從 Visual Studio 2017 開始，會執行掃描僅針對使用者層級的位置。 預設使用者層級位置是 **%USERPROFILE%\Documents\\< Visual Studio 版本\>\Templates\\**。 所產生的範本，這個位置用**專案** > **匯出範本...** 命令時，如果**自動將範本匯入至 Visual Studio**精靈中選取選項。

其他 （非使用者） 的位置，您必須包含指定的位置和範本的其他特性 manifest(.vstman) 檔案。 .Vstman 檔案會產生以及用於範本的.vstemplate 檔案。 如果您安裝您使用.vsix 的擴充功能，您可以完成這需要重新編譯的 Visual Studio 2017 中的擴充功能。 但如果您使用.msi 時，您需要以手動方式進行變更。 如需您需要如何進行這些變更的清單，請參閱**升級至與安裝擴充功能。MSI**本主題稍後。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何更新 VSIX 擴充功能與專案或項目範本  

1.  在 Visual Studio 2017 開啟的方案。 系統會要求您升級的程式碼。 按一下 [確定 **Deploying Office Solutions**]。  
  
2.  在升級完成之後，您可能需要變更安裝目標的版本。 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案，然後選取**安裝目標**] 索引標籤。如果**版本範圍**欄位是 **[14.0]**，按一下 [**編輯**並將它變更為包含 Visual Studio 2017。 例如，您可以將它設定為 **[14.0,15.0]** 安裝擴充功能，Visual Studio 2015 或 Visual Studio 2017，或 **[15.0]** 只 Visual Studio 2017 來安裝它。  
  
3.  編譯程式碼。  
  
4.  關閉 Visual Studio。  
  
5.  安裝此 VSIX。  
  
6.  您可以測試更新，執行下列動作：  
  
    1.  掃描變更的檔案是由下列的登錄機碼啟用：  
  
         **reg 新增 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  加入索引鍵之後，執行**devenv /installvstemplates**。  
  
    3.  重新開啟 Visual Studio。 您應該預期的位置中找到您的範本。  
  
    > [!NOTE]
    >  Visual Studio 擴充性專案範本所不提供登錄機碼存在。 您必須刪除登錄機碼 (並重新執行**devenv /installvstemplates**) 來使用它們。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>其他建議的部署專案和項目範本  
  
-   請避免使用壓縮的範本檔案。 壓縮檔案必須為未壓縮，以便擷取資源和內容的範本，因此將予以 costlier 使用。 相反地，您應該部署專案和項目範本，以加速範本初始化自己目錄下的個別檔案。 VSIX 擴充功能，SDK 建置工作會自動建立 VSIX 檔案時解壓縮 zip 壓縮的任何範本。  
  
-   請避免使用以範本探索期間避免不必要的資源組件載入的封裝/資源識別碼的項目範本名稱、 描述、 圖示或預覽。 相反地，您可以使用當地語系化資訊清單建立的每個地區設定名稱已當地語系化或屬性會使用範本的項目。  
  
-   如果您同時納入做為檔案項目範本，資訊清單產生，可能無法提供您預期的結果。 在此情況下，您必須以手動方式產生資訊清單加入 VSIX 專案。  
  
## <a name="file-changes-in-project-and-item-templates"></a>在專案和項目範本中的檔案變更  
如此您就可以建立新的檔案正確，我們會示範 Visual Studio 2015 和 Visual Studio 2017 新版的範本檔案之間差異的點。  
  
 以下是由 Visual Studio 2015 建立的預設專案.vstemplate 檔案：  
  
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
  
 以下是產生自 VSIX 專案的重建.vstman 檔案 （您可以找到它在 VSIX 專案的資訊清單的目錄中）：  
  
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
  
 所提供的資訊[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)項目維持不變。  **\<VSTemplateContainer >** 元素指向相關聯的範本的.vstemplate 檔案。  
  
 以下是由 Visual Studio 2015 建立的預設項目.vstemplate 檔案：  
  
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
  
 以下是產生自 VSIX 專案的重建.vstman 檔案 （您可以找到它在 VSIX 專案的資訊清單的目錄中）：  
  
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
  
 所提供的資訊 **\<TemplateData >** 項目維持不變。  **\<VSTemplateContainer >** 指向相關聯的範本的.vstemplate 檔案的項目  
  
 如需.vstman 檔案的不同元素的詳細資訊，請參閱[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>安裝擴充功能的升級。MSI

有些 msi 延伸模組會將範本部署到一般的範本位置，如下所示：

- **\<Visual Studio 安裝目錄 > \Common7\IDE\\< ProjectTemplates/項目範本 >**

- **\<Visual Studio 安裝目錄 > \Common7\IDE\Extensions\\< ExtensionName\>\\< 專案/項目範本 >**

如果您的延伸模組執行 MSI 為基礎的部署，您需要手動產生範本資訊清單，並確保它包含在擴充功能安裝程式。 比較上面所列的.vstman 範例和[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。

您應該建立個別的專案和項目範本的資訊清單，它們應該指向根範本目錄指定上述。 建立一個資訊清單，每個擴充功能和地區設定。

## <a name="see-also"></a>另請參閱

[疑難排解範本探索](troubleshooting-template-discovery.md)  
[建立自訂專案與項目範本](creating-custom-project-and-item-templates.md)