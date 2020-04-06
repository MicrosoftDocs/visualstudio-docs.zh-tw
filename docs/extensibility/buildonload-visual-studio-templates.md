---
title: 產生載入屬性與元素(視覺化工作室範本)
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3be4016822ccaaae2f1352f91ecc10f09273a889
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739943"
---
# <a name="buildonload-attribute-and-element"></a>產生載入屬性和元素

指定是否在項目創建後立即生成專案。 **BuildOnLoad**既是一個屬性,也是一個元素。

元素層次結構:

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值

**產生載入**元素需要文本值。 文字必須為`true``false`或 ,指示是否在創建專案後立即生成專案。

## <a name="remarks"></a>備註

**生成載入**是一個可選屬性。 預設值是 `false`。

## <a name="example"></a>範例

以下範例說明了當**BuildOnLoad**用作元素時 C# 樣本的中繼資料:

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

- [組建項目載入元素](buildprojectonload-element-visual-studio-templates.md)
- [樣本內容項目](../extensibility/templatecontent-element-visual-studio-templates.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
