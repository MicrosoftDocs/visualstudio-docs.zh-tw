---
title: " (Visual Studio 範本的專案元素) |Microsoft Docs"
description: 深入瞭解專案專案，以及它如何指定要加入至專案的檔案或目錄。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 652d438d6a0fdf0c42648ded7d3dc9c18b0212ff
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672381"
---
# <a name="project-element-visual-studio-templates"></a> (Visual Studio 範本的專案元素) 
指定要加入至專案的檔案或目錄。

 \<VSTemplate> \<TemplateContent>
 \<Project>

## <a name="syntax"></a>語法

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|說明|
|---------------|-----------------|
|`File`|必要屬性。<br /><br /> 指定範本 *.zip* 檔中的專案檔名稱。|
|`ReplaceParameters`|選擇性屬性。<br /><br /> 布林值，指定在從範本建立專案時，專案檔是否包含必須取代的參數值。 預設值為 `false`。|
|`TargetFileName`|選擇性屬性。<br /><br /> 指定從範本建立專案時的專案檔名稱。|
|`IgnoreProjectParameter`|選擇性屬性。<br /><br /> 指定是否應將專案加入至目前的方案。 如果自訂參數的值 "$*myCustomParameter*$" 存在於參數取代檔案中，則會建立專案，但不會將它新增為目前開啟之方案的一部分。|

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[資料夾](../extensibility/folder-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案的資料夾。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案的檔案。|

### <a name="parent-elements"></a>父元素

|項目|描述|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。|

## <a name="remarks"></a>備註
 `Project` 是 `TemplateContent` 的選擇性子項目。

 `Project`元素用來指定專案，因此只有在專案範本中才有效。

 `Project` 專案可以有 [資料夾](../extensibility/folder-element-visual-studio-project-templates.md) 子項目或 [專案](../extensibility/projectitem-element-visual-studio-project-templates.md) 子項目，但不能同時包含 `Folder` 和 `ProjectItem` 子項目。

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 根據使用者在 [ **新增專案** ] 對話方塊中輸入的名稱，自動重新命名專案檔名稱。 `TargetFileName`如果您想要為以範本建立的專案檔提供替代的檔案名，請使用屬性。

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
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [專案範本 (Visual Studio 專案範本) ](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Visual Studio 專案範本 (資料夾元素) ](../extensibility/folder-element-visual-studio-project-templates.md)
