---
title: GetFrameworkPath 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b907194c4818ff6b867e9d15b795506ef3b77476
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634002"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath 工作

擷取 .NET Framework 組件的路徑。
擷取 .NET Framework 組件的路徑。

## <a name="task-parameters"></a>工作參數

下表說明 `GetFrameworkPath` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`FrameworkVersion11Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 1.1 版組件的路徑 (如果有的話)。 否則傳回 `null`。|
|`FrameworkVersion20Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 2.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|
|`FrameworkVersion30Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 3.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|
|`FrameworkVersion35Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 3.5 版組件的路徑 (如果有的話)。 否則傳回 `null`。|
|`FrameworkVersion40Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含 Framework 4.0 版組件的路徑 (如果有的話)。 否則傳回 `null`。|
|`Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含最新 Framework 版組件的路徑 (如果有的話)。 否則傳回 `null`。|

## <a name="remarks"></a>備註

如果安裝了 .NET 框架的多個版本，則此任務將返回 MSBuild 設計為在它上運行的版本。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

下列範例使用 `GetFrameworkPath` 工作，將 .NET Framework 的路徑儲存在 `FrameworkPath` 屬性中。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkPath>
            <Output
                TaskParameter="Path"
                PropertyName="FrameworkPath" />
        </GetFrameworkPath>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
