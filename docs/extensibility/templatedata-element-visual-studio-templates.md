---
title: " (Visual Studio 範本的 TemplateData 元素) |Microsoft Docs"
description: 瞭解 TemplateData 元素，以及它如何將範本分類，並定義它在 [新增專案] 或 [加入新專案] 對話方塊中顯示的方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 423bcc7b3d902488f268b2d0706cb5126125f37d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895384"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 項目 (Visual Studio 範本)
將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Syntax

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
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

| 元素 | 描述 |
| - | - |
| [名稱](../extensibility/name-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定範本出現在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中的名稱。 |
| [說明](../extensibility/description-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定範本出現在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中的描述。 |
| [圖示](../extensibility/icon-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定影像檔案的路徑和檔案名，此圖示會顯示在範本的 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中。 |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | 必要元素。<br /><br /> 將專案範本分類，使其出現在 [ **新增專案** ] 對話方塊的指定群組中。 |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 將專案範本分類，使其出現在 [ **新增專案** ] 對話方塊的指定子類別下。 |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本識別碼。 |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本群組識別碼。 |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定一個值，用來排列範本，也就是在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的其他範本。 |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否在專案具現化時建立包含的資料夾。 |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定 Visual Studio 專案系統在建立專案或專案時，將為其產生的名稱。 |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定 Visual Studio 專案系統是否會在建立專案或專案時，為其產生預設的名稱。 |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否可將專案建立為暫存專案 (僅 Visual Studio 2017) 。 |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否可在 [**新增專案**] 對話方塊中使用 [**流覽]** 按鈕，讓使用者可以輕鬆地修改儲存新專案的預設目錄。 |
| [Hidden](../extensibility/hidden-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是出現在 [ **新增專案** ] 或 [ **加入新專案** ] 對話方塊中。 |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定將在 [ **新增專案** ] 對話方塊中顯示範本的父類別目錄數目。 |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | 選擇性項目。 |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | 選擇性項目。<br /><br /> 指定專案範本的 [**新增專案**] 對話方塊中的 [**位置**] 文字方塊為 [已啟用]、[已停用] 或 [隱藏]。 |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 如果範本只支援特定的最小版本，以及 .NET Framework 的最新版本，請使用這個元素。 |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是否支援 Web 專案的主版頁面。 |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是否支援 Web 專案的程式碼分隔，或程式碼後端頁面模型。 |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定多個語言的範本是否相同，以及 [**新增專案**] 對話方塊中的 [**語言**] 選項是否可供使用。 |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定專案範本的目標平台。 這個元素會指定用來建立應用程式的專案範本 [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] 。 |

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要元素。<br /><br /> 包含專案範本、專案範本或入門套件的所有中繼資料。|

## <a name="remarks"></a>備註
 `TemplateData` 是必要的元素。

 如果您未包含選擇性元素，則會使用該元素的預設值。

## <a name="example"></a>範例
 下列範例會顯示應用程式專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

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

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
