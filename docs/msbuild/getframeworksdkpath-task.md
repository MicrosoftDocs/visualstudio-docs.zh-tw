---
title: GetFrameworkSdkPath 工作 | Microsoft Docs
description: 瞭解如何使用 MSBuild GetFrameworkSdkPath 工作取出 Windows SDK 的路徑。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0fe468f593d085c10f8d077246af6858d0571fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914637"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath 工作

抓取 Windows 軟體開發套件 (SDK) 的路徑。
## <a name="task-parameters"></a>工作參數

下表說明 `GetFrameworkSdkPath` 工作的參數。
下表說明 `GetFrameworkSdkPath` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 2.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`FrameworkSdkVersion35Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 3.5 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`FrameworkSdkVersion40Path`|選擇性的 `String` 唯讀輸出參數。<br /><br /> 傳回 .NET SDK 4.0 版的路徑 (如果存在的話)。 否則傳回 `String.Empty`。|
|`Path`|選擇性的 `String` 輸出參數。<br /><br /> 包含最新的 .NET SDK 路徑 (如果已有任何版本的話)。 否則傳回 `String.Empty`。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例會使用工作將 `GetFrameworkSdkPath` Windows SDK 的路徑儲存在 `SdkPath` 屬性中。

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
- [工作參考](../msbuild/msbuild-task-reference.md)
