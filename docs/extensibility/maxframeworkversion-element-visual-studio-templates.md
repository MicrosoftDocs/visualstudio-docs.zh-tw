---
title: MaxFrameworkVersion 元素 （Visual Studio 範本） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64f1550db7d2b3613bfa2e9d2da016cc1c6a3e4f
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561784"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 元素 （Visual Studio 範本）

指定最大值範本所需的.NET framework 版本。 它會判斷提供的最大值**目標 Framework 版本**下拉式清單中的**新的專案**對話方塊。 為了讓使用者可以選取 framework 版本，您也必須指定[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)範本的最小.NET Framework 版本。

> [!IMPORTANT]
> 開始在 Visual Studio 2017 版本 15.6、visual**目標 Framework 版本**下拉式清單中不再顯示範本中的篩選條件**範本**一節**新專案**  對話方塊。 相反地，**目標 Framework 版本**下拉式清單中的函式做為所選範本的架構選擇器。

 \<VSTemplate > \<TemplateData > \<MaxFrameworkVersion >

## <a name="syntax"></a>語法

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，以及定義如何顯示在**新的專案**或**加入新項目** 對話方塊。|

## <a name="text-value"></a>文字值
 需要文字值。

 此文字必須是範本所允許的.NET framework 的最高版本號碼。

## <a name="remarks"></a>備註

`MaxFrameworkVersion` 是選擇性項目。 `MaxFrameworkVersion`應該省略項目，除非它是必要項，來為未不慎限制範本的受支援範圍的.NET Framework 版本。 此外，它也應該省略.NET Framework 並不適用的範本。

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

在此範例中，最大版本的.NET Framework 所需的範本，以表示`MaxFrameworkVersion`，是 4.7.1。 使用此範本所建立的專案可以到 4.7.1 的.NET Framework 版本為目標。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
