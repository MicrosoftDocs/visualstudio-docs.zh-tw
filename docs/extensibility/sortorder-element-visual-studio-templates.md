---
title: 排序元素(可視化工作室範本) |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 935d00335a21d3e129e79ce351e554ea93787447
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699961"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 項目 (Visual Studio 範本)
指定用於排列範本的相同類別中的其他樣本的值,因為它顯示在 **「新專案**」或 **「添加新專案」** 對話框中。

 \<VStemplate \<\<>模板数据>排序顺序>

## <a name="syntax"></a>語法

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 將範本分類，並定義該範本在 [新增專案] **** 或 [加入新項目] **** 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 排`integer`序訂單值的 。

## <a name="remarks"></a>備註
  是選擇性元素。 默認值為 100,所有值必須為 10 倍。

 對於`SortOrder`用戶創建的範本,將忽略該元素。 所有使用者創建的範本都按字母順序排序。

 具有低排序訂單值的範本顯示在具有高排序訂單值的範本之前的新**專案**或**新專案對話**框中。

## <a name="example"></a>範例
 下面的範例說明了標準[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類範本的元數據。

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

 此範例中,`SortOrder`元素相對較高。 其他[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]項範`SortOrder`本的值可能`290`低於 ,並且將顯示在"**新建專案"** 對話方塊中此範本之前。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
