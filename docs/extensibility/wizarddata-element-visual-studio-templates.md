---
title: " (Visual Studio 範本的 WizardData 元素) |Microsoft Docs"
description: 瞭解 WizardData 元素，以及它如何指定自訂 XML。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6839a4ac8e53ec70fc88d23525985e8d1b7cccd7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904512"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData 項目 (Visual Studio 範本)

指定自訂 XML

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Syntax

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列章節將說明屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要元素。<br /><br /> 包含專案範本、專案範本或入門套件的所有中繼資料。|

## <a name="text-value"></a>文字值

可選擇使用文字值。

此文字指定要傳遞至 [WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md) 專案中所指定自訂 wizard 擴充功能的自訂 XML。

## <a name="remarks"></a>備註

可以在這個元素中指定任何 XML。 XML 會以參數的形式傳遞至自訂的 wizard 擴充功能，讓擴充功能可以使用此專案的內容。 這項資料不會進行任何驗證。

**WizardData** 元素的內容會以參數形式傳遞（不變），作為方法中參數的字串字典內的參數 `IWizard.RunStarted` 。 字典索引鍵的名稱為 `$wizarddata$` 。

## <a name="example"></a>範例

下列範例說明 c # Windows 應用程式的標準專案範本中繼資料。

```xml
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
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [WizardExtension 元素 (Visual Studio 範本)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [如何：搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)
