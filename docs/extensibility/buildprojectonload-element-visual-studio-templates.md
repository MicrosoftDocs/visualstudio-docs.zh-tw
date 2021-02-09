---
title: " (Visual Studio 範本的 BuildProjectOnload 元素) |Microsoft Docs"
description: 瞭解 BuildProjectOnload 元素，以及它如何在您建立新專案時建立新專案，並將其新增至方案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e2a1f542e89851cb430f8d80934933351e9349e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882267"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a> (Visual Studio 範本的 BuildProjectOnload 元素) 
建立新的專案，並將其新增至方案。 整個方案都不會建立。

元素階層：

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Syntax

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`TemplateData`|將範本分類，並定義該範本在 [ **新增專案** ] 和 [ **加入新專案** ] 對話方塊中的顯示方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是 `true` 或 `false` ，以指出從範本建立新專案時，是否只建立新專案。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `false`。

## <a name="example"></a>範例
 下列範例說明 Visual c # 範本的中繼資料。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [BuildOnLoad 屬性和元素](buildonload-visual-studio-templates.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
