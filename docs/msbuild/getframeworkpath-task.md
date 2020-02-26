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
ms.openlocfilehash: 65a96b59837d04deb0517d3ab79b3b668e036a20
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579649"
---
# <a name="getframeworkpath-task"></a>GetFrameworkPath 工作
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
如果已安裝數個版本的 .NET Framework，此工作會傳回 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 設計來執行的版本。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

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
- [工作參考](../msbuild/msbuild-task-reference.md)
