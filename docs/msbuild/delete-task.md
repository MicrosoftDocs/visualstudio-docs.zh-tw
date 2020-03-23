---
title: Delete 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634275"
---
# <a name="delete-task"></a>Delete 工作

刪除指定的檔案。

## <a name="parameters"></a>參數

下表說明 `Delete` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`DeletedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定已成功刪除的檔案。|
|`Files`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要刪除的檔案。|
|`TreatErrorsAsWarnings`|選擇性的 `Boolean` 參數<br /><br /> 如果是 `true`，即會將錯誤記錄為警告。 預設值是 `false`。|

## <a name="remarks"></a>備註

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

> [!WARNING]
> 在`Delete`任務中使用萬用字元時要小心。 您可以輕鬆地刪除具有 或`$(SomeProperty)\**\*.*``$(SomeProperty)/**/*.*`等運算式的錯誤檔，特別是如果屬性計算為空字串，在這種情況下，`Files`參數可以計算到磁碟機的根目錄，並刪除比您要刪除的多得多。

## <a name="example"></a>範例

下列範例會刪除 *MyApp.pdb* 檔案。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)
