---
title: " (Visual Studio 範本的 WizardExtension 元素) |Microsoft Docs"
description: 深入瞭解 WizardExtension 元素，以及它如何包含用於自訂範本 wizard 的註冊專案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c32f9f2050e04741a2612de30e2718f45c0603de
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061806"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension 項目 (Visual Studio 範本)
包含用於自訂範本 wizard 的註冊專案。

 \<VSTemplate> ... \<WizardExtension>

## <a name="syntax"></a>Syntax

```
<WizardExtension>
    <Assembly>... </Assembly>
    <FullClassName>... </FullClassName>
</WizardExtension>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[組件](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|必要元素。<br /><br /> 指定出現在全域組件快取中之元件的名稱或強式名稱。 元素中必須至少有一個 `Assembly` 元素 `WizardExtension` 。|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|必要元素。<br /><br /> 實介面之類別的完整名稱 `IWizard` 。 元素中必須至少有一個 `FullClassName` 元素 `WizardExtension` 。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|包含專案範本、專案範本或入門套件的所有中繼資料。|

## <a name="remarks"></a>備註
 `WizardExtension` 是 `VSTemplate` 的選擇性子項目。

## <a name="example"></a>範例
 下列範例說明適用于 Windows 應用程式的標準專案範本中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
