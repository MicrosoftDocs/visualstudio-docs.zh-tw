---
title: " (Visual Studio 範本的 ProjectSubType 元素) |Microsoft Docs"
description: 深入瞭解 ProjectSubType 元素，以及它如何將範本分類為 ProjectType 元素中指定之值的子類別。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 02dd5573de12e4626c267fa014f6c7fc8f243b72
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068670"
---
# <a name="projectsubtype-element-visual-studio-templates"></a> (Visual Studio 範本的 ProjectSubType 元素) 
將範本分類為元素中指定之值的子類別 `ProjectType` 。

 \<VSTemplate> \<TemplateData>
 \<ProjectSubType>

## <a name="syntax"></a>Syntax

```xml
<ProjectSubType> SubType </ProjectSubType>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此值會指定範本的子類別。

## <a name="remarks"></a>備註
 `ProjectSubType` 是 `TemplateData` 的選擇性子項目。

 `ProjectSubType`元素提供[ProjectType](../extensibility/projecttype-element-visual-studio-templates.md)專案的子類別。 此值可包含：

- `SmartDevice-NETCFv1`：指定以1.0 版為目標的範本 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 。

- `SmartDevice-NETCFv2`：指定以2.0 版為目標的範本 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 。

  如果範本包含 `ProjectType` 值為的元素 `Web` ， `ProjectSubType` 元素會指定範本的程式設計語言。 這個元素可以有下列值：

- `CSharp`：指定範本建立 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Web 專案或專案。

- `VisualBasic`：指定範本建立 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Web 專案或專案。

## <a name="example"></a>範例
 下列範例顯示以 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 2.0 版為目標之裝置應用程式的專案範本中繼資料 [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] 。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
- [ (Visual Studio 範本的 ProjectType 元素) ](../extensibility/projecttype-element-visual-studio-templates.md)
