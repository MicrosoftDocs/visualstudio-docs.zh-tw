---
title: CreateProperty 工作 | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155e8e6b57cc388e8c2981297be8b26ef5444c1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634314"
---
# <a name="createproperty-task"></a>CreateProperty 工作

將傳入的值填入屬性中。 這允許將值從某個屬性或字串複製至另一個屬性或字串。

## <a name="attributes"></a>屬性

下表說明 `CreateProperty` 工作的參數。

| 參數 | 描述 |
|------------------| - |
| `Value` | 選擇性的 `String` 輸出參數。<br /><br /> 指定要複製至新屬性的值。 |
| `ValueSetByTask` | 選擇性的 `String` 輸出參數。<br /><br /> 包含與 `Value` 參數相同的值。 僅當您希望避免 MSBuild 在跳過封閉目標時設置輸出屬性，因為輸出是最新的，才使用此參數。 |

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

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

- [任務引用](../msbuild/msbuild-task-reference.md)
- [工作](../msbuild/msbuild-tasks.md)
