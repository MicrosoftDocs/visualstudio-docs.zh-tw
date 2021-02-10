---
title: 在專案範本上新增或編輯標籤
description: 了解如何在 Visual Studio 中於專案範本上新增或編輯標籤。
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: a5f8c3f6e96e8e593fe74fd58b3e8bafab0ad88e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950610"
---
# <a name="add-tags-to-project-templates"></a>將標籤新增到專案範本

從 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) 16.1 版 Preview 2 開始，您可以將語言、平台和專案類型標籤新增到您的專案範本。 

標記會在 [ **新增專案** ] 對話方塊的兩個位置中使用：

- 標籤會出現在範本描述下面。

   ![[新增專案] 對話方塊中包含標籤的專案範本](media/npd-item-with-template-tags.png)

- 標籤可讓您搜尋及篩選範本。

   ![[新增專案] 對話方塊中的搜尋及篩選](media/npd-search-and-filter.png)

您可以透過更新 *.vstemplate* XML 檔案來新增標籤。 您可以使用 Visual Studio 內建的範本標籤，或建立自訂範本標籤。 範本標籤只會出現在 Visual Studio 2019 的 [新增專案] 對話方塊中。 範本標籤不會影響範本在先前版本 Visual Studio 中的呈現方式。

## <a name="add-or-edit-tags"></a>新增或編輯標籤

當您採取下列其中一個動作時，您可以在專案範本的 *.vstemplate* XML 中新增或編輯標籤：

* 使用 [匯出範本] 嚮導來[建立新的專案範本](how-to-create-project-templates.md)。
* [更新現有的專案範本](how-to-update-existing-templates.md)。
* [建立新的 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)。

## <a name="syntax"></a>Syntax

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>屬性

您可以在進階使用者案例中使用下列選擇性屬性：

|屬性|描述|
|---------------|-----------------|
|`Package`|指定 Visual Studio 套件識別碼的 GUID。|
|`ID`|指定 Visual Studio 資源識別碼。|

語法：

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>元素

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(必要) 將範本分類，並定義範本在 [新增專案] 對話方塊或 [加入新項目] 對話方塊中的顯示方式。|

## <a name="text-value"></a>文字值

除非您使用 `Package` 和 `ID` 屬性，否則需要文字值。

文字能提供範本的名稱。

## <a name="built-in-tags"></a>內建標籤

Visual Studio 提供內建標籤清單。 當您新增內建標籤時，標籤會呈現當地語系化資源。 

下列清單顯示 Visual Studio 中可用的內建標籤。 對應值顯示在括弧中。

| 語言標記 | 平臺標記 | 專案類型標記 |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | 雲端 (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | 主控台 (`console`) |
| F# (`fsharp`) | iOS (`ios`) | 桌面 (`desktop`) |
| Java (`java`) | Linux (`linux`) | 擴充 (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | 遊戲 (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| 查詢語言 (`querylanguage`) | Windows (`windows`) | 程式庫 (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Machine Learning (`machinelearning`) |
| Visual Basic (`visualbasic`) | | 行動 (`mobile`) |
| | | Office (`office`) |
| | | 其他 (`other`) |
| | | 服務 (`service`) |
| | | 測試 (`test`) |
| | | UWP (`uwp`) |
| | | Web (`web`) |

## <a name="example"></a>範例

下列範例顯示 Visual C# 應用程式專案範本的中繼資料：

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
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

- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](creating-project-and-item-templates.md)
- [自訂專案和項目範本](customizing-project-and-item-templates.md)
- [開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)
