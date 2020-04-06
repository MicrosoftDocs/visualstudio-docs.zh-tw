---
title: VSTemplate 元素(視覺工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651e8b6dbbe11c450b105f3185e7e987bb30da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697872"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate 元素(視覺化工作室範本)
包含有關專案範本、專案範本或初學者工具組的所有元資料。

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
| `Type` | 將範本標識為專案範本或專案範本。 此屬性可以具有`Project`或`Item`的值。 |
| `Version` | 指定範本的版本號。 的[!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]樣本,並且[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]`Version`具有的屬性`3.0.0`值 。 |

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定對範本進行分類的資料,並定義範本在 **「新專案**」或 **「添加新專案**」對話框中的顯示方式。|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|必要元素。<br /><br /> 指定範本的內容。|
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|選擇性項目。|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|選擇性項目。|

### <a name="parent-elements"></a>父元素
 無。

## <a name="remarks"></a>備註
 該`VSTemplate`元素是 *.vstemplate*檔案的根元素。

## <a name="example"></a>範例
 下面的範例顯示了[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]應用程式的專案範本的元數據。

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
- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
