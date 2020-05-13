---
title: GetFrameworkSdkPath 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d021bdb485846749ea2c7e9dfe483e09738fda46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633989"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath 工作

檢索到 Windows 軟體發展工具組 （SDK） 的路徑。
## <a name="task-parameters"></a>工作參數

下表說明 `GetFrameworkSdkPath` 工作的參數。
下表說明 `GetFrameworkSdkPath` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 2.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`FrameworkSdkVersion35Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 3.5 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`FrameworkSdkVersion40Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 4.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含最新的 .NET SDK 路徑 (如果已有任何版本的話)。 否則傳回 `String.Empty`。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

下面的示例使用`GetFrameworkSdkPath`該任務將 Windows SDK 的路徑存儲在屬性中`SdkPath`。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
