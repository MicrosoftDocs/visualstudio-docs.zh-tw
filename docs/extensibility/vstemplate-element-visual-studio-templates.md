---
title: VSTemplate 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9dc06b287485d857c18214ade500e63ff8032b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953227"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 項目 （Visual Studio 範本）
包含有關專案範本、 項目範本或入門套件的所有中繼資料。

## <a name="syntax"></a>語法

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
|-----------| - |
| `Type` | 識別為專案範本或項目範本的範本。 這個屬性可以具有的值`Project`或`Item`。 |
| `Version` | 指定範本的版本號碼。 中的範本[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]並[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]有`Version`屬性值`3.0.0`。 |

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定分類的範本，並定義中的顯示方式的資料**新的專案**或是**加入新項目** 對話方塊。|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要項目。<br /><br /> 指定範本的內容。|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|選擇性項目。|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|選擇性項目。|

### <a name="parent-elements"></a>父元素
 無。

## <a name="remarks"></a>備註
 `VSTemplate`元素是根元素 *.vstemplate*檔案。

## <a name="example"></a>範例
 下列範例顯示的專案範本的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs</ProjectItem>
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
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)