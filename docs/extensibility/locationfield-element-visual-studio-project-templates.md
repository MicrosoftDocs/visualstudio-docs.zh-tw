---
title: LocationField 項目 (Visual Studio 專案範本)
titleSuffix: ''
description: 瞭解 LocationField 元素，以及它如何指定專案範本的 [新增專案] 對話方塊位置文字方塊是否已啟用、停用或隱藏。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cbd0d6ee6ede29be35437125f614512ff3bbeab3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915179"
---
# <a name="locationfield-element-visual-studio-project-templates"></a> (Visual Studio 專案範本的 LocationField 元素) 
指定是否針對專案範本啟用、停用或隱藏 [**新增專案**] 對話方塊中的 [**位置**] 文字方塊。

 \<VSTemplate> \<TemplateData>
 \<LocationField>

## <a name="syntax"></a>Syntax

```
<LocationField> Enabled/Disabled/Hidden </LocationField>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義它在 **新專案** 中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 有效的文字值為：

- `Enabled`，指定啟用 [**新增專案**] 對話方塊的 [**位置**] 方塊。

- `Disabled`，指定 [**新增專案**] 對話方塊的 [**位置**] 方塊已停用。

- `Hidden`，指定隱藏 [**新增專案**] 對話方塊的 [**位置**] 方塊。

## <a name="remarks"></a>備註
 預設值是 `Enabled`。

 [**新增專案**] 對話方塊中的 [**位置**] 文字方塊可讓使用者變更儲存新專案的預設目錄。

 `Location`只有當基礎專案系統支援時，才會接受元素中指定的值。

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
        <LocationField>Disabled</LocationField>
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
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
