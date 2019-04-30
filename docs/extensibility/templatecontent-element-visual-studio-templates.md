---
title: TemplateContent 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c27f9ce239d5d82dc972186912266cea0d4f1ddf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62432274"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent 項目 (Visual Studio 範本)

指定範本的內容。

項目階層架構：

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>語法

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|指定是否要從範本建立專案時，建置方案。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定多專案範本的組織和內容。|
|[Project](../extensibility/project-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定要加入至專案檔案或目錄。|
|[參考](../extensibility/references-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定所需的項目範本的組件參考。|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|選擇性項目。<br /><br /> 指定範本中包含的檔案。|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|選擇性項目。<br /><br /> 指定從範本建立專案或項目時要使用的任何自訂參數。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要項目。<br /><br /> 包含專案範本、 項目範本，或入門套件的所有中繼資料。|

## <a name="remarks"></a>備註
 `TemplateContent` 是必要項目。

## <a name="example"></a>範例
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式。

```xml
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