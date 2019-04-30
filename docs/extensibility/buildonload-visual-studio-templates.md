---
title: BuildOnLoad 屬性和項目 （Visual Studio 範本）
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 760dc8bb501fb345cbee686818ad0b4d6698a684
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891645"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad 屬性和項目

指定是否要在建立之後，立即建置專案。 **BuildOnLoad**是屬性和項目。

項目階層架構：

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>項目語法

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值

文字值是為了**BuildOnLoad**項目。 文字必須是`true`或`false`，指出是否要在建立之後，立即建置專案。

## <a name="remarks"></a>備註

**BuildOnLoad**是選擇性的屬性。 預設值為 `false`。

## <a name="example"></a>範例

下列範例說明的中繼資料C#範本時**BuildOnLoad**做為項目：

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
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

- [BuildProjectOnload 項目](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent 項目](../extensibility/templatecontent-element-visual-studio-templates.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)