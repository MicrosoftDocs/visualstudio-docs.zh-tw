---
title: " (Visual Studio 範本的 BuildOnLoad 屬性和元素) "
titleSuffix: ''
description: 瞭解 BuildOnLoad 屬性和元素，以及它如何指定是否要在建立專案之後立即建立專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fe0fa745ef611395abe6244c0e207271b182cb4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927323"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad 屬性和元素

指定是否要在建立專案之後立即建立專案。 **BuildOnLoad** 同時是屬性和元素。

元素階層：

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>元素語法

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值

**BuildOnLoad** 元素需要文字值。 文字必須是 `true` 或 `false` ，指出是否要在建立專案之後立即建立專案。

## <a name="remarks"></a>備註

**BuildOnLoad** 是選擇性屬性。 預設值是 `false`。

## <a name="example"></a>範例

下列範例說明使用 **BuildOnLoad** 做為元素時，c # 範本的中繼資料：

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

- [BuildProjectOnload 元素](buildprojectonload-element-visual-studio-templates.md)
- [TemplateContent 元素](../extensibility/templatecontent-element-visual-studio-templates.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
