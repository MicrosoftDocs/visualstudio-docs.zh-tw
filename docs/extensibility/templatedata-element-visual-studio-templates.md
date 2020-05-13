---
title: 範本資料元素(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699198"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData 項目 (Visual Studio 範本)
將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。

 \<>,範本\<>模板数据

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
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

| 元素 | 描述 |
| - | - |
| [名稱](../extensibility/name-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定樣本的名稱,因為它顯示在新**專案**或「**新增新項目**」對話框中。 |
| [說明](../extensibility/description-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定樣本的說明,如範本顯示在 **「新專案**」或「**新增新項目**」對話框中。 |
| [圖示](../extensibility/icon-element-visual-studio-templates.md) | 必要元素。<br /><br /> 指定用作樣本的圖示的影像檔的路徑和檔名,該圖示顯示在新**專案**或「**添加新專案」** 對話框中。 |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | 必要元素。<br /><br /> 對專案範本進行分類,使其顯示在 **「新專案」** 對話方塊中的指定群組下。 |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 對專案範本進行分類,使其顯示在 **「新專案」** 對話方塊中的指定子類別下。 |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本代碼。 |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定樣本組 ID。 |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定用於排列範本的相同類別中的其他樣本的值,因為它顯示在 **「新專案**」或 **「添加新專案」** 對話框中。 |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否在項目的實體化時建立包含資料夾。 |
| [預設名稱](../extensibility/defaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定可視化工作室專案系統在創建專案或專案時將生成的名稱。 |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定視覺化工作室專案系統在建立專案或專案時是否將生成預設名稱。 |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定是否可以將項目創建為臨時專案(僅限 Visual Studio 2017)。 |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定 **「瀏覽」** 按鈕在 **「新項目**」對話方塊中是否可用,以便使用者可以輕鬆地修改儲存新專案的預設目錄。 |
| [隱藏](../extensibility/hidden-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定樣本是否顯示在 **「新專案**」或 **「新增新專案」** 對話方塊中。 |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定將在 **「新項目」** 對話框中顯示範本的父類別數。 |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | 選擇性項目。 |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | 選擇性項目。<br /><br /> 指定新**項目**對話框中**的**文字盒是否已為專案範本啟用、關閉或隱藏。 |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 如果範本僅支援 .NET Framework 的特定最小版本和更高版本(如果有),則使用此元素。 |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定樣本是否支援 Web 專案的母版頁。 |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定範本是支援 Web 專案的代碼分離還是代碼背後的頁面模型。 |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定多語言的範本是否相同,以及 **「新建項目**」對話框中 **「語言」** 選項是否可用。 |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | 選擇性項目。<br /><br /> 指定專案範本的目標平台。 此元素指定專案範本用於創建[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]應用。 |

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要元素。<br /><br /> 包含專案範本、專案範本或初學者工具組的所有元資料。|

## <a name="remarks"></a>備註
 `TemplateData`是必需的元素。

 如果不包括可選元素,則使用該元素的預設值。

## <a name="example"></a>範例
 下面的範例顯示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式的專案範本的元數據。

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
