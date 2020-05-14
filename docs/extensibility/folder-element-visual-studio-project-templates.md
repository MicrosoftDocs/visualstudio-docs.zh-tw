---
title: 資料夾元素(可視化工作室專案範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb256b8be0dd9ce68f193750bf3ff5a383d5f073
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711458"
---
# <a name="folder-element-visual-studio-project-templates"></a>資料夾元素(視覺化工作室專案樣本)
指定將新增到項目的資料夾。

 \<樣本>\<範本內容>\<專案>\<資料夾>

## <a name="syntax"></a>語法

```
<Folder Name="Project Folder">
    <Folder> ... </Folder>
    <ProjectItem> ... </ProjectItem>
</Folder>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`Name`|必要屬性。<br /><br /> 項目資料夾的名稱。|
|`TargetFolderName`|選擇性屬性。<br /><br /> 指定從範本建立專案時要為資料夾提供的名稱。 此屬性可用於使用參數替換創建資料夾名稱或使用無法直接在 *.zip*檔案中直接使用的國際字串命名資料夾。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`Folder`|指定要新增到項目的資料夾。 `Folder`元素可以包含子`Folder`元素。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要加入項目的檔案。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[專案](../extensibility/project-element-visual-studio-templates.md)|[樣本內容](../extensibility/templatecontent-element-visual-studio-templates.md)的選擇子元素 。|

## <a name="remarks"></a>備註
 `Folder`是`Project`的可選子項。

 可以使用以下任一方法將項目項目組織到樣本中的資料夾中:

- 將資料夾包含在範本 *.zip*檔中,並`ProjectItem`透過在元素中指定檔案路徑`Folder`(沒有元素)將它們添加到 *.vstemplate*檔案中的專案。 這是建議的方法。 例如：

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 將資料夾包含在範本 *.zip*檔中,並將它們添加`Folder`到包含元素的 *.vstemplate*檔中的專案。 例如：

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 不要在範本 *.zip*檔中包含資料夾,`TargetFileName``ProjectItem`而是使用 元素的屬性添加資料夾。 例如：

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>範例
 下面的範例展示[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 應用程式的專案樣本的中繼資料。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyTemplate.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <Folder Name="Properties">
                <ProjectItem>AssemblyInfo.cs</ProjectItem>
                <ProjectItem>Resources.resx</ProjectItem>
                <ProjectItem>Resources.Designer.cs</ProjectItem>
                <ProjectItem>Settings.settings</ProjectItem>
                <ProjectItem>Settings.Designer.cs</ProjectItem>
            </Folder>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)
