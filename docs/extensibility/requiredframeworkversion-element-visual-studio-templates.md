---
title: RequiredFrameworkVersion 元素 （Visual Studio 範本） |Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40eefc62eef318bcd9c52a1cbbb966377b3616f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62805806"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 元素 （Visual Studio 範本）

指定最小值範本所需的.NET framework 版本。 它會導致**目標 Framework 版本**下拉式清單，以顯示在**新的專案**對話方塊。 `RequiredFrameworkVersion`元素也會決定可用的下拉式清單中的最小值。

> [!IMPORTANT]
> 開始在 Visual Studio 2017 版本 15.6、visual**目標 Framework 版本**下拉式清單中不再顯示範本中的篩選條件**範本**一節**新專案**  對話方塊。 相反地，下拉式清單中做為架構的選擇器選取的範本。

 \<VSTemplate> \<TemplateData> \<RequiredFrameworkVersion>

## <a name="syntax"></a>語法

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，以及定義如何顯示在**新的專案**或**加入新項目** 對話方塊。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是.NET Framework 所需的範本的最小版本號碼。

## <a name="remarks"></a>備註

`RequiredFrameworkVersion` 是選擇性項目。 範本支援特定的最低版本 （和更新版本，如果有的話） 時，才使用這個元素的.NET framework。 如果您指定`RequiredFrameworkVersion`項目和您的範本不支援特定的最低版本.NET framework**目標 Framework 版本**它並不適用時，會顯示下拉式清單。

## <a name="example"></a>範例

下列範例說明一種標準的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類別樣板。

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

在此範例中，最小版本的.NET Framework 所需的範本，以表示`RequiredFrameworkVersion`，是 3.0。 使用此範本所建立的專案可以從 3.0 開始的.NET Framework 版本為目標。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [以特定的.NET Framework 版本為目標](../ide/visual-studio-multi-targeting-overview.md)
