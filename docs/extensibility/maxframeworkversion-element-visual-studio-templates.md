---
title: " (Visual Studio 範本的 MaxFrameworkVersion 元素) |Microsoft Docs"
description: 瞭解 MaxFrameworkVersion 元素，以及它如何指定範本所需之 .NET Framework 的最大版本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 09ddccece8261a331277d1c143054305f0d08d7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943201"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a> (Visual Studio 範本的 MaxFrameworkVersion 元素) 

指定範本所需之 .NET Framework 的最大版本。 它會決定 [**新增專案**] 對話方塊的 [**目標 Framework 版本**] 下拉式清單中可用的最高值。 為了讓使用者能夠選取架構版本，您也必須指定 [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) 作為範本的最小 .NET Framework 版本。

> [!IMPORTANT]
> 從 Visual Studio 2017 15.6 版開始，[**目標 Framework 版本**] 下拉式清單不再是 [**新增專案**] 對話方塊的 [**範本**] 區段中顯示之範本的篩選。 相反地，[ **目標 Framework 版本** ] 下拉式清單會作為所選範本的架構選擇器。

 \<VSTemplate> \<TemplateData>
 \<MaxFrameworkVersion>

## <a name="syntax"></a>Syntax

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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

 此文字必須是範本所允許之 .NET Framework 的最高版本號碼。

## <a name="remarks"></a>備註

 是選擇性元素。 `MaxFrameworkVersion`除非必要，否則應該省略元素，因此不會不慎限制範本的 .NET Framework 版本支援範圍。 如果 .NET Framework 不適用於範本，也應該省略此參數。

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

在此範例中，範本所需之 .NET Framework 的最大版本（以表示） `MaxFrameworkVersion` 為4.7.1。 使用此範本建立的專案可將 .NET Framework 版本的目標設為4.7.1。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和專案範本](../ide/creating-project-and-item-templates.md)
