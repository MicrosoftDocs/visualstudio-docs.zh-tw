---
title: AssignTargetPath 工作 | Microsoft Docs
description: 使用 MSBuild AssignTargetPath 工作接受檔案清單，並新增 TargetPath 屬性（如果尚未指定）。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9f3a46b16bc689e0753b806c4239544e1ddbd73f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964936"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath 工作

此工作接受檔案清單，並新增 `<TargetPath>` 屬性 (若尚未指定)。

## <a name="task-parameters"></a>工作參數

下表說明 `AssignTargetPath` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`RootFolder`|選擇性 `string` 輸入參數。<br /><br /> 包含有目標連結的資料夾路徑。|
|`Files`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸入參數。<br /><br /> 包含傳入的檔案清單。|
|`AssignedFiles`|選擇性<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`output 參數。<br /><br /> 包含產生的檔案清單。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

下列範例會執行 `AssignTargetPath` 工作來設定專案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyProject">
        <AssignTargetPath
RootFolder="Resources"
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
        </AssignTargetPath>
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
