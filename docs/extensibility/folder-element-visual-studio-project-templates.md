---
title: ) 的 Visual Studio 專案範本 (資料夾元素 |Microsoft Docs
description: 瞭解 Folder 元素，以及它如何指定將新增至專案的資料夾。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Folder
helpviewer_keywords:
- Folder element [Visual Studio project templates]
ms.assetid: 558e3d41-0db5-4c44-82bb-6bb87892b093
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9b655308760d64f97c168e8000972142f159ec3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968225"
---
# <a name="folder-element-visual-studio-project-templates"></a>Visual Studio 專案範本 (資料夾元素) 
指定將新增至專案的資料夾。

 \<VSTemplate> \<TemplateContent>
 \<Project>
 \<Folder>

## <a name="syntax"></a>Syntax

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
|`Name`|必要屬性。<br /><br /> 專案資料夾的名稱。|
|`TargetFolderName`|選擇性屬性。<br /><br /> 指定從範本建立專案時，要提供資料夾的名稱。 這個屬性適用于使用參數取代來建立資料夾名稱，或使用無法直接在 *.zip* 檔案中使用的國際字串來命名資料夾。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|`Folder`|指定要加入至專案的資料夾。 `Folder` 元素可以包含子 `Folder` 元素。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|指定要加入至專案的檔案。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[專案](../extensibility/project-element-visual-studio-templates.md)|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)的選擇性子項目。|

## <a name="remarks"></a>備註
 `Folder` 是的選擇性子系 `Project` 。

 您可以使用下列任何一種方法，將專案專案組織為範本中的資料夾：

- 將資料夾包含在 *.zip* 檔案中，並在專案中指定檔案的路徑 `ProjectItem` （不含任何元素），以將它們新增至 .vstemplate 檔案中的專案 `Folder` 。 這是建議的方法。 例如：

     `...`

     `<ProjectItem>\Folder\item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 將資料夾包含在 *.zip* 檔案中，並將它們新增至 *.vstemplate* 檔案中具有專案的專案 `Folder` 。 例如：

     `...`

     `<Folder name="Folder">`

     `<ProjectItem>item.cs</ProjectItem>`

     `</Folder>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

- 請勿在範本 *.zip* 檔案中包含資料夾，但請使用 `TargetFileName` 元素的屬性來加入資料夾 `ProjectItem` 。 例如：

     `...`

     `<ProjectItem TargetFileName="\Folder\item.cs">item.cs</ProjectItem>`

     `<ProjectItem>Form1.cs</ProjectItem>`

     `...`

## <a name="example"></a>範例
 下列範例說明適用于 Windows 應用程式之專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

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
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [ProjectItem 項目 (Visual Studio 項目範本)](../extensibility/projectitem-element-visual-studio-item-templates.md)
