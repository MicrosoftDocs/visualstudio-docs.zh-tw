---
title: " (Visual Studio 範本的 SupportsMasterPage 元素) |Microsoft Docs"
description: 瞭解 SupportsMasterPage 元素，以及它如何指定是否在 [加入新專案] 對話方塊中啟用 [選取主版頁面] 核取方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsMasterPage
helpviewer_keywords:
- <SupportsMasterPage> element [Visual Studio Templates]
- SupportsMasterPage element [Visual Studio Templates]
ms.assetid: ce877a6a-9bba-4fd9-92fb-0a8dfec9e75b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3b779b3626c4ff47fe798fa9f4ff2e7bc9c7ac8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056034"
---
# <a name="supportsmasterpage-element-visual-studio-templates"></a>SupportsMasterPage 項目 (Visual Studio 範本)
指定是否在 [**加入新專案**] 對話方塊中啟用 [**選取主版頁面**] 核取方塊。

 \<VSTemplate> \<TemplateData>
 \<SupportsMasterPage>

## <a name="syntax"></a>Syntax

```
<SupportsMasterPage> true/false </SupportsMasterPage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|指定將範本分類的資料，並定義該範本在 [ **新增專案** ] 或 [ **新增專案** ] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是 `true` 或 `false` ，表示 [**加入新專案**] 對話方塊中是否已啟用 [**選取主版頁面**] 核取方塊。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `false`。

 `SupportsMasterPage`元素僅適用于 Web 專案範本。

## <a name="example"></a>範例
 下列範例說明包含主版頁面支援的 Web 專案中繼資料。

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsMasterPage>true</SupportsMasterPage>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
