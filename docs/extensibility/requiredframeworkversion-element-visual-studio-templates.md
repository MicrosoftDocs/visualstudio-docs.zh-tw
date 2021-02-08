---
title: RequiredFrameworkVersion 項目 (Visual Studio 範本)
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 211393ea65f7ca31f80134c48863b0092478b3f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836978"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a> (Visual Studio 範本的 RequiredFrameworkVersion 元素) 

指定範本所需之 .NET Framework 的最小版本。 這會導致 [**新增專案**] 對話方塊中顯示 [**目標 Framework 版本**] 下拉式清單。 `RequiredFrameworkVersion`元素也會決定下拉式清單中可用的最小值。

> [!IMPORTANT]
> 從 Visual Studio 2017 15.6 版開始，[**目標 Framework 版本**] 下拉式清單不再是 [**新增專案**] 對話方塊的 [**範本**] 區段中顯示之範本的篩選。 相反地，下拉式清單會作為所選範本的架構選擇器。

 \<VSTemplate> \<TemplateData>
 \<RequiredFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是範本所需之 .NET Framework 的最小版本號碼。

## <a name="remarks"></a>備註

 是選擇性元素。 只有在範本支援特定的最小版本 (和更新版本（如果 .NET Framework 的任何) ）時，才使用這個元素。 如果您指定專案 `RequiredFrameworkVersion` ，而您的範本不支援特定的最小 .NET Framework 版本，則會顯示 [ **目標 Framework 版本** ] 下拉式清單（不適用）。

## <a name="example"></a>範例

下列範例說明標準類別範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```xml
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>3.0</RequiredFrameworkVersion>
        <MaxFrameworkVersion>4.7.1</MaxFrameworkVersion>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

在此範例中，範本所需之 .NET Framework 的最小版本（以表示 `RequiredFrameworkVersion` ）是3.0。 使用此範本所建立的專案可將目標設定為從3.0 開始的 .NET Framework 版本。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)
