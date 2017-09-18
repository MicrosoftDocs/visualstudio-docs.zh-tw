---
title: "升級自訂專案和項目範本，適用於 Visual Studio&quot;15&quot;|Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>升級自訂專案與 Visual Studio 2017 的項目範本
從 Visual Studio 2017 開始，Visual Studio 會變更，以探索專案和項目已由.vsix 或.msi 安裝的範本的方式。 如果您擁有使用自訂的專案或項目範本的擴充功能，您需要更新您的擴充功能。 本主題說明您必須。  
  
 這項變更會影響只有 Visual Studio 2017。 它不會影響舊版的 Visual Studio。  
  
 如果您想要建立專案或項目範本為 VSIX 擴充功能的一部分，請參閱[建立自訂專案和項目範本](../extensibility/creating-custom-project-and-item-templates.md)。  
  
## <a name="template-scanning"></a>範本掃瞄  
 先前， **devenv /setup**或**devenv /installvstemplates**掃描以尋找專案和項目範本的本機磁碟。 從預覽 4 開始，將會執行掃描只會針對使用者層級位置 (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**) 所用的範本所產生**檔案] / [匯出範本**命令。  
  
 針對其他 （非使用者） 的位置，您必須包含指定的位置和範本的其他特性 manifest(.vstman) 檔案。 .Vstman 檔案會產生以及用於範本的.vstemplate 檔。 如果您安裝使用.vsix 擴充功能，您可以完成這需要重新編譯的 Visual Studio 2017 中的擴充功能。 但如果您使用.msi 時，您需要以手動方式進行變更。 如需如何進行這些變更的清單，請參閱**擴充功能安裝與升級。MSI**稍後在本主題中。  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>如何更新 VSIX 擴充功能與專案或項目範本  
 此程序說明如何以 Visual Studio 2017
1.  在 Visual Studio 2017 開啟的方案。 系統會要求您升級的程式碼。 按一下 [確定]。  
  
2.  在升級完成之後，您可能需要變更安裝目標版本。 在 VSIX 專案中，開啟 source.extension.vsixmanifest 檔案，然後選取**安裝目標** 索引標籤。 如果**版本範圍**欄位是**[14.0]**，按一下 **編輯**並將它變更為包含 Visual Studio 2017。 例如，您可以將它設定為**[14.0,15.0]**安裝擴充功能，Visual Studio 2015 或 Visual Studio 2017，或**[15.0]**將其安裝到只是 Visual Studio 2017。  
  
3.  編譯程式碼。  
  
4.  關閉 Visual Studio。  
  
5.  安裝 VSIX。  
  
6.  您可以透過下列方式測試更新︰  
  
    1.  掃描變更的檔案是由下列登錄機碼啟用︰  
  
         **reg 新增 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  加入機碼之後，執行**devenv /installvstemplates**。  
  
    3.  重新開啟 Visual Studio。 您應該預期的位置中找到您的範本。  
  
    > [!NOTE]
    >  登錄機碼存在時為 Visual Studio 擴充性專案範本。 您必須刪除登錄機碼 (並重新執行**devenv /installvstemplates**) 來使用它們。  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>部署專案和項目範本的其他建議  
  
-   請避免使用壓縮的範本檔案。 壓縮檔案需要未壓縮，以便擷取資源和內容的範本，因此它們會 costlier 使用。 相反地，您應該部署專案和項目範本，以加速範本初始化自己目錄下的個別檔案。 VSIX 擴充功能，SDK 建置工作會自動將解壓縮任何壓縮的範本建立 VSIX 檔案時。  
  
-   請避免使用套件/資源識別碼的項目範本名稱、 描述、 圖示或預覽，以避免不必要的資源組件載入範本探索期間。 相反地，您可以使用當地語系化資訊清單來建立每個地區設定使用當地語系化的名稱或屬性的範本項目。  
  
-   如果還有範本做為檔案項目，產生資訊清單可能會讓您預期的結果。 在此情況下，您必須手動產生資訊清單加入 VSIX 專案。  
  
## <a name="file-changes-in-project-and-item-templates"></a>在專案和項目範本中的檔案變更  
 我們將說明 Visual Studio 2015 版本與範本檔案中，Visual Studio"15"版本之間差異的點，因此您可以正確地建立新的檔案。  
  
 以下是建立 Visual Studio 2015 的預設專案的.vstemplate 檔︰  
  
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
  
 以下是產生的 VSIX 專案重建.vstman 檔案 （您可以找到它的 VSIX 專案的資訊清單的目錄中）︰  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 所提供的資訊[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)項目維持不變。 ** \<VSTemplateContainer >**元素指向相關聯範本的.vstemplate 檔。  
  
 以下是建立 Visual Studio 2015 預設項目.vstemplate 檔︰  
  
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
  
 以下是產生的 VSIX 專案重建.vstman 檔案 （您可以找到它的 VSIX 專案的資訊清單的目錄中）︰  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 所提供的資訊** \<TemplateData >**項目維持不變。 ** \<VSTemplateContainer >**元素指向相關聯範本的.vstemplate 檔  
  
 如需.vstman 檔案的不同元素的詳細資訊，請參閱[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>安裝擴充功能的升級。MSI  
 有些以 MSI 為基礎的延伸模組會將範本部署到一般範本位置，如下所示︰  
  
-   **\<Visual Studio 安裝目錄 > \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Visual Studio 安裝目錄 > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 如果您的擴充功能來執行以 MSI 為基礎的部署，您需要手動產生範本資訊清單，並確保包含延伸模組安裝程式中。 您應該比較上面所列的.vstman 範例和[Visual Studio 範本資訊清單結構描述參考](../extensibility/visual-studio-template-manifest-schema-reference.md)。 若要查看您需要包含  
  
 您應該建立個別的專案和項目範本的資訊清單，並應該指向根範本目錄指定上述。 您應該建立一份資訊清單，每個延伸模組和地區設定。  
  
## <a name="troubleshooting-template-installation"></a>範本安裝疑難排解  
 如果您遇到問題，部署您的專案或項目範本，您可以啟用診斷記錄。  
  
1.  執行下列命令來設定登錄機碼，若要啟用記錄︰  
  
     **reg 新增 HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  啟動 Visual Studio，並啟動 [新增專案] 和 [新項目] 對話方塊來初始化這兩個範本樹狀結構。 範本記錄現在會出現在**%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**。 每個範本樹狀目錄中初始化會將項目附加至這個記錄檔。  
  
 記錄檔包含下列欄位︰  
  
-   **FullPathToTemplate**，其具有下列值︰  
  
    -   1 代表資訊清單為基礎的部署  
  
    -   0 代表磁碟為基礎的部署  
  
-   **TemplateFileName**  
  
-   其他範本內容
