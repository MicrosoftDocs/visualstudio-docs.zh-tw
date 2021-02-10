---
title: " (的 SortOrder 元素 Visual Studio 範本) |Microsoft Docs"
description: 瞭解 SortOrder 元素，以及它如何指定用來排列範本的值（在 [新增專案] 或 [加入新專案] 對話方塊中）。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2a086f2ae678541ce28e9ede874c4198e349f438
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942915"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 項目 (Visual Studio 範本)
指定一個值，用來排列範本，也就是在 [ **新增專案** ] 或 [ **加入新** 專案] 對話方塊中顯示的其他範本。

 \<VSTemplate> \<TemplateData>
 \<SortOrder>

## <a name="syntax"></a>Syntax

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

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

 `integer`表示排序次序值的。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值為100，而且所有值都必須是10的倍數。

 `SortOrder`使用者建立的範本會忽略元素。 所有使用者建立的範本會依字母順序排序。

 具有低排序次序值的範本會出現在 [ **新增專案** ] 或 [ **新增** 專案] 對話方塊中，然後才會出現在具有高排序次序值的範本之前。

## <a name="example"></a>範例
 下列範例說明標準類別範本的中繼資料 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 。

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class template.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>290</SortOrder>
        <DefaultName>MyClass</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

 在此範例中， `SortOrder` 元素相對較高。 其他 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案範本的值可能會 `SortOrder` 小於 `290` ，而且會出現在 [ **新增專案** ] 對話方塊中的這個範本之前。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
