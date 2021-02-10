---
title: Warning 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用警告工作，根據評估的條件陳述式來記錄組建期間的警告。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f31ad26b6efffa540ecae6a61f0f7ff12115cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933800"
---
# <a name="warning-task"></a>Warning 工作

在建置期間，根據評估的條件陳述式來記錄警告。

## <a name="parameters"></a>參數

 下表說明 `Warning` 工作的參數。

| 參數 | Description |
|---------------| - |
| `Code` | 選擇性的 `String` 參數。<br /><br /> 要與警告建立關聯的警告碼。 |
| `File` | 選擇性的 `String` 參數。<br /><br /> 指定相關檔案 (如果有的話)。 如果未提供任何檔案，則會使用包含 Warning 工作的檔案。 |
| `HelpKeyword` | 選擇性的 `String` 參數。<br /><br /> 要與此警告關聯的 Help 關鍵字。 |
| `Text` | 選擇性的 `String` 參數。<br /><br /> 如果參數評估為，MSBuild 會記錄的警告文字 `Condition` `true` 。 |

## <a name="remarks"></a>備註

 此工作可 `Warning` 讓 MSBuild 專案先檢查必要的設定或屬性是否存在，然後再繼續進行下一個組建步驟。

 如果 `Warning` 工作的 `Condition` 參數評估為 `true`，則會記錄 `Text` 參數的值，而建置會繼續執行。 如果 `Condition` 參數不存在，則會記錄警告文字。 如需有關記錄的詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

 下列程式碼範例會檢查命令列上所設定的屬性。 如果未設定任何屬性，專案就會引發警告事件，並記錄 `Warning` 工作的 `Text` 參數值。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>另請參閱

- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
- [專案檔案架構參考](../msbuild/msbuild-project-file-schema-reference.md)
