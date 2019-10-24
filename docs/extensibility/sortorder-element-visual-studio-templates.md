---
title: SortOrder 元素（Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2875bcb4583c1d2ec47a935d1a8bb4f0de109a92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72719918"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 項目 (Visual Studio 範本)
指定一個值，用來排列範本，在相同類別目錄中的其他範本中，因為它出現在 [**新增專案**] 或 [**加入新專案**] 對話方塊中。

 \<VSTemplate > \<TemplateData > \<SortOrder >

## <a name="syntax"></a>語法

```
<SortOrder> ... </SortOrder>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案] 或 [加入新項目] 對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 表示排序次序值的 `integer`。

## <a name="remarks"></a>備註
 `SortOrder` 是選擇性項目。 預設值為100，且所有值都必須為10的倍數。

 使用者建立的範本會忽略 `SortOrder` 元素。 所有使用者建立的範本都會依字母順序排序。

 具有較低排序次序值的範本會在具有高排序次序值的範本之前，出現在 [**新增專案**] 或 [**新增加入專案**] 對話方塊中。

## <a name="example"></a>範例
 下列範例說明標準 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 類別範本的中繼資料。

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

 在此範例中，`SortOrder` 元素相當高。 其他 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 專案範本可能會有小於 `290` 的 `SortOrder` 值，而且會出現在 [**新增專案**] 對話方塊中的這個範本之前。

## <a name="see-also"></a>請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)