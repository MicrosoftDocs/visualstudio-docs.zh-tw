---
title: ShowByDefault 元素（Visual Studio 範本）
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2405e46a7f1ed8d2e4ae33b1b58ec44e06aa7d3b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720107"
---
# <a name="showbydefault-element-visual-studio-templates"></a>ShowByDefault 元素（Visual Studio 範本）
如果 `false`，則指定範本只會顯示在指定的[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)之下。

 \<.Vstemplate > \<TemplateData > \<ShowByDefault >

## <a name="syntax"></a>語法

```
<ShowByDefault> true/false </ShowByDefault>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子項目
 無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|將範本分類，並定義該範本在 [新增專案] 或 [加入新項目] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是 `true` 或 `false`。 如果為 true，請指定範本將會針對所有專案類型顯示。 如果為 false，則範本只會顯示在指定的 `TemplateGroupID` 之下。

## <a name="remarks"></a>備註
 `ShowByDefault` 是選擇性項目。 預設值是 `true`。

## <a name="example"></a>範例
 下列範例說明 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範本的中繼資料。

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ShowByDefault>false</ShowByDefault>
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

## <a name="see-also"></a>請參閱
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [TemplateGroupID 元素 (Visual Studio 範本)](../extensibility/templategroupid-element-visual-studio-templates.md)