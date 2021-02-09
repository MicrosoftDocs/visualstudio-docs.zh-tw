---
title: " (Visual Studio 範本的 ProjectType 元素) |Microsoft Docs"
description: 深入瞭解 ProjectType 元素，以及它如何將專案範本分類，使其出現在 [新增專案] 或 [加入新專案] 對話方塊中。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectType
helpviewer_keywords:
- ProjectType element [Visual Studio project templates]
ms.assetid: ccf9d83f-c7f3-49c7-a31f-e1f22bec004c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a90c8de2fca62ef303ce8055993d8e2f6d230493
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910892"
---
# <a name="projecttype-element-visual-studio-templates"></a> (Visual Studio 範本的 ProjectType 元素) 
將專案範本分類，使其出現在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊的指定群組中。

> [!WARNING]
> 從 Visual Studio 2012 開始，c + + 支援專案範本。 Visual Studio 2010 及更舊版本中的 c + + 不支援這些功能。

 \<VSTemplate> \<TemplateData>
 \<ProjectType>

## <a name="syntax"></a>Syntax

```xml
<ProjectType> CSharp/VisualBasic/VC/Web </ProjectType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此值指定範本將建立的專案類型，而且必須包含下列其中一個值：

- `CSharp`：指定範本建立 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案或專案。

- `VisualBasic`：指定範本建立 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 專案或專案。

- `Web`：指定範本建立 Web 專案或專案。 如果 `ProjectType` 元素包含此值，則會在 ProjectSubType 元素中定義專案或專案的語言， [ (Visual Studio 範本) ](../extensibility/projectsubtype-element-visual-studio-templates.md)。

## <a name="remarks"></a>備註
 `ProjectType` 是 `TemplateData` 的必要子項目。

 元素的值 `ProjectType` 會指定範本位於 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中的位置。 例如， `ProjectType` 值為的範本 `CSharp` 會出現在 [**新增專案**] 對話方塊中的 [ **Visual c #** ] 節點底下。

 您可以使用 [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) 元素來指定範本子類型。

## <a name="example"></a>範例
 下列範例會顯示應用程式專案範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
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
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [ (Visual Studio 範本的 ProjectSubType 元素) ](../extensibility/projectsubtype-element-visual-studio-templates.md)
