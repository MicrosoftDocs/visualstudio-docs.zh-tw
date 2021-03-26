---
title: SupportsCodeSeparation 項目 (Visual Studio 範本)
titleSuffix: ''
description: 若要在 [加入新專案] 對話方塊中啟用 [將程式碼放入個別檔案] 核取方塊，請瞭解 SupportsCodeSeparation 元素及其指定方式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsCodeSeparation
helpviewer_keywords:
- SupportsCodeSeparation element [Visual Studio Templates]
- <SupportsCodeSeparation> element [Visual Studio Templates]
ms.assetid: 8112aac8-a269-40e5-b92b-9b9a6ff5a542
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 699d38f712885d1e2b08a111baa7db75fb7829da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056125"
---
# <a name="supportscodeseparation-element-visual-studio-templates"></a>SupportsCodeSeparation 項目 (Visual Studio 範本)
指定是否在 [**加入新專案**] 對話方塊中，啟用 [將程式 **代碼放在個別檔案中**] 核取方塊。

 \<VSTemplate> \<TemplateData>
 \<SupportsCodeSeparation>

## <a name="syntax"></a>Syntax

```
<SupportsCodeSeparation> true/false </SupportsCodeSeparation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **新增** 專案] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是 `true` 或 `false` ，表示在 [**加入新專案**] 對話方塊中是否已啟用 [將程式 **代碼放入個別** 檔案] 核取方塊。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `false`。

 `SupportsCodeSeparation`元素僅適用于 Web 專案範本。

 程式碼分隔（或程式碼後端頁面模型）可讓您將標記保留在一個檔案中，並將程式碼放在另一個檔案中。 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 和其他 .NET 語言使用此模型。

## <a name="example"></a>範例
 下列範例會指定 **在個別檔案選項中顯示位置代碼** 。

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
        <SupportsCodeSeparation>true</SupportsCodeSeparation>
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
