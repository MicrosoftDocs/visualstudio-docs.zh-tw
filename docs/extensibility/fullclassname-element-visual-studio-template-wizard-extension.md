---
title: 全質名稱元素(VS 樣本精靈副檔名)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e533fdf5b5497b17949581801721136b18bc2d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711424"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>全類名稱元素(可視化工作室範本精靈副檔名)
實現`IWizard`介面的類的完全限定名稱。

 \<VSTemplate>\<嚮導延伸>...\<全類名稱>

## <a name="syntax"></a>語法

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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|包含用於自定義範本嚮導的註冊元素。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文本指定實現介面的`IWizard`類。 指定的類必須存在於[程式集](../extensibility/assembly-element-visual-studio-template-wizard-extension.md)元素指定的程式集中。

## <a name="remarks"></a>備註
 `FullClassName` 是 `WizardExtension` 的必要子項目。

## <a name="example"></a>範例
 下面的範例展示[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]Windows 應用程式的標準項目樣本的中繼資料。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [如何:將精靈與專案樣本一起使用](../extensibility/how-to-use-wizards-with-project-templates.md)
