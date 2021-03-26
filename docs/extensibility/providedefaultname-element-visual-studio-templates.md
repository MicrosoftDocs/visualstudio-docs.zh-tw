---
title: " (Visual Studio 範本的 ProvideDefaultName 元素) |Microsoft Docs"
description: 瞭解 ProvideDefaultName 元素，以及它如何指定 Visual Studio 是否會在 [加入新專案] 或 [新增專案] 對話方塊中產生預設 Visual Studio 名稱。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName
helpviewer_keywords:
- ProvideDefaultName element [Visual Studio project templates]
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d29ca3075ee6e5ef031bb360ecfd10d6cb341c26
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068631"
---
# <a name="providedefaultname-element-visual-studio-templates"></a> (Visual Studio 範本的 ProvideDefaultName 元素) 
指定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案系統是否會在 [ **加入新專案** ] 或 [ **新增專案** ] 對話方塊中，產生範本的預設名稱。

 \<VSTemplate> \<TemplateData>
 \<ProvideDefaultName>

## <a name="syntax"></a>Syntax

```xml
<ProvideDefaultName> true/false </ProvideDefaultName>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是 `true` 或 `false` ，指出是否要在 [ **加入新專案** ] 或 [ **新增專案** ] 對話方塊中產生範本的預設名稱。

## <a name="remarks"></a>備註
  是選擇性元素。 預設值是 `true`。

 如果專案 `ProvideDefaultName` 為 `false` ，[**加入新專案**] 和 [**新增專案**] 對話方塊的 [**名稱**] 方塊就會包含值 `<Enter_name>` 。

 使用 [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) 元素可在 [ **加入新專案** ] 和 [ **新增專案** ] 對話方塊中，指定專案或專案的預設名稱。 當元素的值 `ProvideDefaultName` 為時 `true` ，省略專案的專案會在對話方塊中 `DefaultName` 填入範本的名稱，也就是 [name](../extensibility/name-element-visual-studio-templates.md) 元素的值。

## <a name="example"></a>範例
 下列程式碼範例會將 `ProvideDefaultName` 元素設定為 `false` 。

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProvideDefaultName>false</ProvideDefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem>MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
