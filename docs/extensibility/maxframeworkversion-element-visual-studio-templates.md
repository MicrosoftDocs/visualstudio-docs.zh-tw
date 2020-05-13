---
title: 最大框架版本元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c3acf9c40499417fe180ce470224824cc89a113
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702626"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>最大框架版本元素(視覺化工作室範本)

指定範本所需的 .NET 框架的最大版本。 它確定**新專案****對話框的目標框架版本**下拉清單中可用的最高值。 為了使用戶能夠選擇框架版本,還必須將[「必需框架版本」](../extensibility/requiredframeworkversion-element-visual-studio-templates.md)指定為範本的最低 .NET 框架版本。

> [!IMPORTANT]
> 從 Visual Studio 2017 版本 15.6 開始,**目標框架版本**下拉清單不再是 **「新專案」** 對話方塊「**範本**」 部分中顯示範本的篩選器。 相反,**目標框架版本**下拉清單功能為選取範本的框架選取器。

 \<樣本>\<範本資料>\<最大框架版本>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義如何在 **「新專案**」或「**新增新項目**」對話框中顯示範本。|

## <a name="text-value"></a>文字值
 需要文字值。

 文本必須是範本允許的 .NET 框架的最高版本號。

## <a name="remarks"></a>備註

 是選擇性元素。 除非`MaxFrameworkVersion`需要,否則應省略該元素,以免無意中限制範本支援的 .NET Framework 版本範圍。 如果 .NET 框架不適用於範本,也應省略它。

## <a name="example"></a>範例

下面的範例說明了標準[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]類範本的元數據。

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

在此範例中,範本(由表示)`MaxFrameworkVersion`所需的 .NET 框架的最大版本為 4.7.1。 使用此範本建立的專案可以定位 .NET 框架版本,最多 4.7.1。

## <a name="see-also"></a>另請參閱

- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立項目與專案樣本](../ide/creating-project-and-item-templates.md)
