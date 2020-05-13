---
title: 必需框架版本元素(可視化工作室範本) |微軟文件
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 060ebc0633de67d93257e24c2dff24d2aa0970da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701504"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>必要框架版本元素(視覺化工作室範本)

指定範本所需的 .NET 框架的最小版本。 它會導致新**項目**對話框中顯示 **「目標框架版本**」下拉清單。 該`RequiredFrameworkVersion`元素還確定下拉清單中可用的最低值。

> [!IMPORTANT]
> 從 Visual Studio 2017 版本 15.6 開始,**目標框架版本**下拉清單不再是 **「新專案」** 對話方塊「**範本**」 部分中顯示範本的篩選器。 相反,下拉清單充當所選範本的框架選取器。

 \<>\<樣本>\<需要框架版本>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|必要元素。<br /><br /> 對樣本進行分類,並定義如何在 **「新專案**」或「**新增新項目**」對話框中顯示範本。|

## <a name="text-value"></a>文字值
 需要文字值。

 文本必須是範本所需的 .NET 框架的最低版本號。

## <a name="remarks"></a>備註

 是選擇性元素。 僅當範本支援 .NET Framework 的特定最小版本(以及更高版本(如果有)時,才使用此元素。 如果指定`RequiredFrameworkVersion`元素,並且範本不支援 .NET 框架的特定最小版本,**則目標框架版本**下拉清單將在不適用時顯示。

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

在此範例中,範本(由表示)`RequiredFrameworkVersion`所需的 .NET 框架的最小版本為 3.0。 使用此範本創建的專案可以定位 .NET 框架版本,從 3.0 開始。

## <a name="see-also"></a>另請參閱

- [視覺化工作室範本架構參考](../extensibility/visual-studio-template-schema-reference.md)
- [建立專案與項目範本](../ide/creating-project-and-item-templates.md)
- [Framework 目標概觀](../ide/visual-studio-multi-targeting-overview.md)
