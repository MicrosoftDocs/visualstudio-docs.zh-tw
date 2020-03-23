---
title: Error 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5dd3214c9575a34e9265c33061b024648a221c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634223"
---
# <a name="error-task"></a>Error 工作

停止組建，並根據評估的條件陳述式來記錄錯誤。

## <a name="parameters"></a>參數

下表說明 `Error` 工作的參數。

| 參數 | 描述 |
|---------------| - |
| `Code` | 選擇性的 `String` 參數。<br /><br /> 與錯誤相關聯的錯誤碼。 |
| `File` | 選擇性的 `String` 參數。<br /><br /> 包含錯誤的檔案名稱。 如果沒有提供檔案名稱，將會使用包含 Error 工作的檔案。 |
| `HelpKeyword` | 選擇性的 `String` 參數。<br /><br /> 要與錯誤相關聯的 Help 關鍵字。 |
| `Text` | 選擇性的 `String` 參數。<br /><br /> 如果`Condition`參數計算為`true`，則 MSBuild 記錄的錯誤文本。 |

## <a name="remarks"></a>備註

該`Error`任務允許 MSBuild 專案向記錄器發出錯誤文本並停止生成執行。

如果 `Condition` 參數評估為 `true`，即會停止組建，並記錄錯誤。 如果 `Condition` 參數不存在，則會記錄錯誤，並停止組建執行。 如需記錄的詳細資訊，請參閱[取得建置記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

下列程式碼範例會確認已設定所有必要的屬性。 若未設定，專案就會引發錯誤事件，並記錄 `Error` 工作的 `Text` 參數值。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
