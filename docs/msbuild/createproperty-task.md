---
title: CreateProperty 工作 | Microsoft Docs
description: 使用 MSBuild CreateProperty 工作，以傳入的值填入屬性，允許將值從一個屬性或字串複製到另一個。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ea412f67629998eab035b8cca79111659ab8a0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901367"
---
# <a name="createproperty-task"></a>CreateProperty 工作

將傳入的值填入屬性中。 這允許將值從某個屬性或字串複製至另一個屬性或字串。

## <a name="attributes"></a>屬性

下表說明 `CreateProperty` 工作的參數。

| 參數 | Description |
|------------------| - |
| `Value` | 選擇性的 `String` 輸出參數。<br /><br /> 指定要複製至新屬性的值。 |
| `ValueSetByTask` | 選擇性的 `String` 輸出參數。<br /><br /> 包含與 `Value` 參數相同的值。 只有當您想要避免 MSBuild 在因為輸出是最新狀態時，由 MSBuild 設定 output 屬性時，才使用此參數。 |

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例使用 `CreateProperty` 工作，以使用 `SourceFilename` 和 `SourceFileExtension` 屬性值組合建立 `NewFile` 屬性。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

執行專案之後，`NewFile` 屬性的值是 *Module1.vb*。

## <a name="see-also"></a>另請參閱

- [工作參考](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
