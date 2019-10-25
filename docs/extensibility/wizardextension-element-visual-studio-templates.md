---
title: WizardExtension 元素（Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardExtension
helpviewer_keywords:
- WizardExtension element [Visual Studio Templates]
- <WizardExtension> element [Visual Studio Templates]
ms.assetid: d54b01c1-50f5-4b65-828c-686e2321cc8c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cfd46573f70b31559f9d6c4749c142d763537764
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748941"
---
# <a name="wizardextension-element-visual-studio-templates"></a>WizardExtension 項目 (Visual Studio 範本)
包含自訂範本 wizard 的註冊元素。

 \<VSTemplate > ... \<WizardExtension >

## <a name="syntax"></a>語法

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

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|[Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)|必要項目。<br /><br /> 指定出現在全域組件快取中之元件的名稱或強式名稱。 @No__t_1 元素中必須至少有一個 `Assembly` 元素。|
|[FullClassName](../extensibility/fullclassname-element-visual-studio-template-wizard-extension.md)|必要項目。<br /><br /> 實 `IWizard` 介面之類別的完整名稱。 @No__t_1 元素中必須至少有一個 `FullClassName` 元素。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[.Vstemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|包含專案範本、專案範本或入門套件的所有中繼資料。|

## <a name="remarks"></a>備註
 `WizardExtension` 是 `VSTemplate` 的選擇性子項目。

## <a name="example"></a>範例
 下列範例說明適用于 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows 應用程式的標準專案範本中繼資料。

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

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [如何︰搭配專案範本使用精靈](../extensibility/how-to-use-wizards-with-project-templates.md)