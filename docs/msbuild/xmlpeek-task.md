---
title: XmlPeek 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 XmlPeek 工作，從 XML 檔案傳回 XPath 查詢所指定的值。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9d387d44ba06bb3a5a8ef5e73e2d8900b356996e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964858"
---
# <a name="xmlpeek-task"></a>XmlPeek 工作

從 XML 檔案傳回 XPath 查詢所指定的值。

## <a name="parameters"></a>參數

 下表說明 `XmlPeek` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Namespaces`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢前置詞的命名空間。|
|`Query`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢。|
|`Result`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含此工作所傳回的結果。|
|`XmlContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XML 輸入。|
|`XmlInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 將 XML 輸入指定為檔案路徑。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

以下是要讀取的 XML 範例檔案 `settings.config` ：

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

在此範例中，如果您想要讀取 `value` ，請使用如下所示的程式碼：

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

使用 XML 命名空間時，您可以使用 `Namespaces` 參數，如下列範例所示。 使用輸入 XML 檔案 `XMLFile1.xml` ：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<class AccessModifier='public' Name='test' xmlns:s='http://nsurl'>
  <s:variable Type='String' Name='a'>This</s:variable>
  <s:variable Type='String' Name='b'>is</s:variable>
  <s:variable Type='String' Name='c'>Sparta!</s:variable>
  <method AccessModifier='public static' Name='GetVal' />
</class>
```

以及專案檔 `Target` 中定義的下列專案：

```xml
  <Target Name="TestPeek" BeforeTargets="Build">
    <!-- Find the Name attributes -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/@Name"
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value1" />
    </XmlPeek>
    <Message Text="@(value1)"/>
    <!-- Find 'variable' nodes (XPath query includes ".") -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/."
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value2" />
    </XmlPeek>
    <Message Text="@(value2)"/>
  </Target>
```

輸出包含來自目標的下列 `TestPeek` 內容：

```output
  TestPeek output:
  a;b;c
  <s:variable Type="String" Name="a" xmlns:s="http://nsurl">This</s:variable>;<s:variable Type="String" Name="b" xmlns:s="http://nsurl">is</s:variable>;<s:variable Type="String" Name="c" xmlns:s="http://nsurl">Sparta!</s:variable>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
- [XPath 查詢語法](https://wikipedia.org/wiki/XPath)
