---
title: SortOrder 項目 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder
helpviewer_keywords:
- SortOrder element [Visual Studio Templates]
- <SortOrder> element [Visual Studio Templates]
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4477d5ff193df40eaf84175b09b5e28a521f72c7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696333"
---
# <a name="sortorder-element-visual-studio-templates"></a>SortOrder 項目 (Visual Studio 範本)
指定值，因為它會出現在其中一個用來排列的範本，在相同類別中，其他範本之間**新的專案**或是**加入新項目** 對話方塊。

 \<VSTemplate> \<TemplateData> \<SortOrder>

## <a name="syntax"></a>語法

```
<SortOrder> ... </SortOrder>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性
 無。

### <a name="child-elements"></a>子元素
 無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義該範本在 [新增專案]  或 [加入新項目]  對話方塊中顯示的方式。|

## <a name="text-value"></a>文字值
 需要文字值。

 `integer`表示排序順序值。

## <a name="remarks"></a>備註
 `SortOrder` 是選擇性項目。 預設值是 100，而且所有的值必須是 10 的倍數。

 `SortOrder`項目會被忽略的使用者建立的範本。 所有使用者建立的範本會依字母順序都排序。

 具有低的排序順序值的範本會出現在其中一個**新的專案**或**新加入的項目**有高的排序次序值的範本之前的對話方塊。

## <a name="example"></a>範例
 下列範例說明一種標準的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類別樣板。

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

 在此範例中，`SortOrder`項目是相當高。 可能是其他[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]項目範本會有`SortOrder`值低於`290`而且會出現在此範本之前**新項目** 對話方塊。

## <a name="see-also"></a>另請參閱
- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)