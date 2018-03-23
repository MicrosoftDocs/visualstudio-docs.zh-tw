---
title: MaxFrameworkVersion 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: edc3f443423a6c70815c4f32f1b2c91d5ead85b6
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 項目 (Visual Studio 範本)

指定範本所需的.NET Framework 的最新版本。 它會判斷在可用的最大值**目標 Framework 版本**下拉式清單中的**新專案**對話方塊。 為了讓使用者可以選取 framework 版本，您也必須指定[RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)做為範本的最小.NET Framework 版本。

> [!IMPORTANT]
> 從 Visual Studio 2017 版本 15.6，**目標 Framework 版本**下拉式清單中不再顯示範本中的篩選**範本**區段**新的專案**對話方塊。 相反地，**目標 Framework 版本**下拉式清單中做為架構的選擇器選取的範本。

 \<VSTemplate> \<TemplateData> \<MaxFrameworkVersion>

## <a name="syntax"></a>語法

```xml
<MaxFrameworkVersion> ... </MaxFrameworkVersion>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要項目。<br /><br /> 將範本分類，並定義要如何顯示在**新專案**或**加入新項目** 對話方塊。|

## <a name="text-value"></a>文字值
 需要文字值。

 文字必須是最高的版本號碼的.NET Framework 所允許的範本。

## <a name="remarks"></a>備註

`MaxFrameworkVersion` 是選擇性項目。 `MaxFrameworkVersion`應該省略項目，除非它是必要項，來為未不慎限制範本的受支援範圍的.NET Framework 版本。 此外，它也應該省略.NET Framework 並不適用的範本。

## <a name="example"></a>範例

下列範例說明標準的中繼資料[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類別樣板。

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

在此範例中，最大版本的.NET Framework 所需的範本，以表示`MaxFrameworkVersion`，是 4.7.1。 使用此範本建立的專案可以 4.7.1 到.NET Framework 版本為目標。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
