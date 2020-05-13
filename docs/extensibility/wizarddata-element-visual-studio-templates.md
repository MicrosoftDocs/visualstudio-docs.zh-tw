---
title: 嚮導數據元素(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3f9d2e971d944b964f4b194d1324ff960fbd24
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740387"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData 項目 (Visual Studio 範本)

指定自訂 XML

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>語法

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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|必要元素。<br /><br /> 包含專案範本、專案範本或初學者工具組的所有元資料。|

## <a name="text-value"></a>文字值

可選擇使用文字值。

此文字指定要傳遞到[精靈延伸](../extensibility/wizardextension-element-visual-studio-templates.md)元素中指定的自訂精靈擴展。

## <a name="remarks"></a>備註

可以在此元素中指定任何 XML。 XML 將作為參數傳遞給自定義嚮導擴展,允許擴展使用此元素的內容。 未對此數據執行驗證。

**嚮導資料**元素的內容`IWizard.RunStarted`作為 方法中參數位串字典中的參數傳遞,不變。 字典鍵名稱`$wizarddata$`。

## <a name="example"></a>範例

下面的範例展示 C# Windows 應用程式的標準項目範本的中繼資料。

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
