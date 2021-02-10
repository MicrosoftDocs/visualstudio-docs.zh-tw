---
title: 'FullClassName 元素 (VS template wizard 擴充) '
description: 瞭解 FullClassName 元素，以及它是實 IWizard 介面之類別的完整名稱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d23bb194dfadd202cf2899b1834f3b6ceeaa2b3f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968199"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>Visual Studio 範本 wizard 擴充功能 (的 FullClassName 元素) 
實介面之類別的完整名稱 `IWizard` 。

 \<VSTemplate> \<WizardExtension>
... \<FullClassName>

## <a name="syntax"></a>Syntax

```xml
<FullClassName>ClassName</FullClassName>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|包含用於自訂範本 wizard 的註冊專案。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字指定實介面的類別 `IWizard` 。 指定的類別必須存在於 [assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) 元素所指定的元件中。

## <a name="remarks"></a>備註
 `FullClassName` 是 `WizardExtension` 的必要子項目。

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
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何：搭配專案範本使用嚮導](../extensibility/how-to-use-wizards-with-project-templates.md)
