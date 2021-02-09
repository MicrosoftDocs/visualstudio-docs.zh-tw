---
title: SupportsLanguageDropDown 項目 (Visual Studio 範本)
titleSuffix: ''
description: 瞭解 SupportsLanguageDropDown 元素，以及它如何指定多個語言的 Web 專案範本是否相同，以及是否已啟用語言選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 79141361253df4e1ccaf29ff15332d534ceade84
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898087"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown 項目 (Visual Studio 範本)

指定多個語言的 Web 專案範本是否相同，以及是否在 [**加入新專案**] 對話方塊中啟用 [**語言**] 選項。

 \<VSTemplate> \<TemplateData>
 \<SupportsLanguageDropDown>

## <a name="syntax"></a>Syntax

```xml
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值

 需要文字值。

 此文字必須是 `true` 或 `false` ，指出是否可以從 [**加入新專案**] 對話方塊中使用 [**語言**] 選項。

## <a name="remarks"></a>備註

  是選擇性元素。 預設值是 `false`。

 `SupportsLanguageDropDown`元素僅適用于 Web 專案範本。

 如果這個元素的值設定為，則 `true` 所有程式設計語言的專案範本都相同，而且在 [**加入新專案**] 對話方塊中會啟用 [**語言**] 選項。 此選項可讓您選擇要從範本建立之新專案的程式設計語言。

## <a name="example"></a>範例

 下列範例會指定顯示 [ **語言** ] 下拉式清單選項。

```xml
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
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
