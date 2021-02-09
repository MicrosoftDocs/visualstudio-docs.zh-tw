---
title: " (Visual Studio 範本的 CreateInPlace 元素) "
description: 瞭解 CreateInPlace 元素，以及它如何指定是否要建立專案，並在特定或暫存位置執行參數取代。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa138923f8d23c59613ce1bbc51460fd3c8c9acb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870333"
---
# <a name="createinplace-element-visual-studio-templates"></a> (Visual Studio 範本的 CreateInPlace 元素) 
指定是否要在指定的位置建立專案並執行參數取代，或在暫存位置中執行參數取代，然後將專案儲存至指定的位置。

 \<VSTemplate> \<TemplateData>
 \<CreateInPlace>

## <a name="syntax"></a>Syntax

```
<CreateInPlace> true/false </CreateInPlace>
```

## <a name="attributes-and-elements"></a>屬性和元素
 下列章節說明屬性、子元素和父元素。

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

 此文字必須是 `true` 或 `false`。 如果為 `true` ，則會建立專案，並在 [ **新增專案** ] 對話方塊中指定的位置執行參數取代。 如果為 `false` ，則會在暫存位置中執行參數取代，然後將專案複製到指定的位置。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `true`。

## <a name="example"></a>範例
 下列範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本的中繼資料。

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateInPlace>false</CreateInPlace>
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
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
