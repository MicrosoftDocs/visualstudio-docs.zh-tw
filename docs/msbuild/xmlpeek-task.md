---
title: XmlPeek 工作 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094664"
---
# <a name="xmlpeek-task"></a>XmlPeek 工作

從 XML 檔案傳回 XPath 查詢所指定的值。

## <a name="parameters"></a>參數

 下表說明 `XmlPeek` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`Namespaces`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢前置詞的命名空間。|
|`Query`|選擇性的 `String` 參數。<br /><br /> 指定 XPath 查詢。|
|`Result`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含此工作所傳回的結果。|
|`XmlContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XML 輸入。|
|`XmlInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 將 XML 輸入指定為檔案路徑。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。



## <a name="example"></a>範例

下面是要讀取的 XML`settings.config`檔示例：

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

在此示例中，如果要讀取`value`，請使用如下所示的代碼：

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

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
