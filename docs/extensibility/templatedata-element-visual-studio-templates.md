---
title: TemplateData 元素（Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b122857a4d916379c070e923ed0753b01287f08b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718860"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 項目 (Visual Studio 範本)
將範本分類，並定義該範本在 [新增專案] 或 [加入新項目] 對話方塊中顯示的方式。

 \<.Vstemplate > \<TemplateData >

## <a name="syntax"></a>語法

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子項目

| 項目 | 描述 |
| - | - |
| [名稱](../extensibility/name-element-visual-studio-templates.md) | 必要項目。<br /><br /> 指定範本出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中的名稱。 |
| [說明](../extensibility/description-element-visual-studio-templates.md) | 必要項目。<br /><br /> 指定範本出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中的描述。 |
| [圖示](../extensibility/icon-element-visual-studio-templates.md) | 必要項目。<br /><br /> 指定影像檔案的路徑和檔案名，做為範本出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中的圖示。 |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | 必要項目。<br /><br /> 將專案範本分類，使其出現在 [**新增專案**] 對話方塊中的指定群組底下。 |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 將專案範本分類，使其出現在 [**新增專案**] 對話方塊中指定的子類別之下。 |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本識別碼。 |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本群組識別碼。 |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定一個值，用來排列範本，在相同類別目錄中的其他範本中，因為它出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中。 |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否要在具現化專案時建立包含的資料夾。 |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定在建立專案或專案時，Visual Studio 專案系統將為其產生的名稱。 |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定 Visual Studio 專案系統是否會在建立專案或專案時，產生其預設名稱。 |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否可以將專案建立為暫存專案（僅限 Visual Studio 2017）。 |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定 [**新增專案**] 對話方塊中是否有 [**流覽]** 按鈕，讓使用者可以輕鬆地修改儲存新專案的預設目錄。 |
| [隱含](../extensibility/hidden-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是否會出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中。 |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定要在 [**新增專案**] 對話方塊中顯示範本的父類別目錄數目。 |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | 選擇性項目。 |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | 選擇性項目。<br /><br /> 指定專案範本的 [**新增專案**] 對話方塊中的 [**位置**] 文字方塊是否為 [已啟用]、[已停用] 或 [隱藏]。 |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 如果範本僅支援特定的最小版本，以及 .NET Framework 的更新版本，請使用此元素。 |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是否支援 Web 專案的主版頁面。 |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是否支援 Web 專案的程式碼分離或程式碼後置頁面模型。 |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定多個語言的範本是否相同，以及是否可從 [**新增專案**] 對話方塊使用 [**語言**] 選項。 |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定專案範本的目標平台。 此元素會指定用來建立 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 應用程式的專案範本。 |

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[.Vstemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要項目。<br /><br /> 包含專案範本、專案範本或入門套件的所有中繼資料。|

## <a name="remarks"></a>備註
 `TemplateData` 是必要的元素。

 如果您未包含選擇性專案，則會使用該元素的預設值。

## <a name="example"></a>範例
 下列範例會顯示 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 應用程式之專案範本的中繼資料。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)