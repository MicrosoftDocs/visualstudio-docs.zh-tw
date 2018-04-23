---
title: RequiredFrameworkVersion 項目 （Visual Studio 範本） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adc1a138c50c0fe13962f6601449eb3498d90398
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 項目 (Visual Studio 範本)

指定範本所需的.NET framework 最低版本。 它會導致**目標 Framework 版本**下拉式清單中顯示**新專案**對話方塊。 `RequiredFrameworkVersion`元素也會決定可用的下拉式清單中的最小值。

> [!IMPORTANT]
> 從 Visual Studio 2017 版本 15.6，**目標 Framework 版本**下拉式清單中不再顯示範本中的篩選**範本**區段**新的專案**對話方塊。 相反地，下拉式清單中做為架構的選擇器選取的範本。

 \<VSTemplate > \<TemplateData > \<RequiredFrameworkVersion >

## <a name="syntax"></a>語法

```xml
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>
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

 文字必須是.NET Framework 所需的範本的最小版本號碼。

## <a name="remarks"></a>備註

`RequiredFrameworkVersion` 是選擇性項目。 使用此項目，只有當此範本支援特定的最低版本 （和更新版本，如果有的話） 的.NET framework。 如果您指定`RequiredFrameworkVersion`項目和您的範本不支援特定的.NET Framework 中，最小版本**目標 Framework 版本**下拉式清單中顯示時不適用。

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

在此範例中，這個範本時，所需的.NET framework 的最低版本以`RequiredFrameworkVersion`，為 3.0。 使用此範本建立的專案可以開始從 3.0 的.NET Framework 版本為目標。

## <a name="see-also"></a>另請參閱

- [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案和項目範本](../ide/creating-project-and-item-templates.md)
- [以特定的 .NET Framework 版本為目標](../ide/targeting-a-specific-dotnet-framework-version.md)
