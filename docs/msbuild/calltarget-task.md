---
title: CallTarget 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26d29c236b89172ab6dc456be97016b98f2cae19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094554"
---
# <a name="calltarget-task"></a>CallTarget 工作

叫用專案檔內指定的目標。

## <a name="task-parameters"></a>工作參數

 下表說明 `CallTarget` 工作的參數。

| 參數 | 描述 |
|---------------------------| - |
| `RunEachTargetSeparately` | 選擇性 `Boolean` 輸入參數。<br /><br /> 如果`true`，MSBuild 引擎將按目標調用一次。 如果`false`調用 MSBuild 引擎一次以生成所有目標。 預設值是 `false`。 |
| `TargetOutputs` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所有建置目標的輸出。 |
| `Targets` | 選擇性的 `String[]` 參數。<br /><br /> 指定要建置的一或多個目標。 |
| `UseResultsCache` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即傳回快取的結果 (如果有的話)。<br /><br /> **注意**：執行 MSBuild 工作時，會在範圍 (ProjectFileName, GlobalProperties)[TargetNames] 內快取它的結果，當作組建項目清單。 |

## <a name="remarks"></a>備註

 如果在 `Targets` 中指定的目標失敗，而 `RunEachTargetSeparately` 是 `true`，則工作會繼續建置其餘的目標。

 如果要生成預設目標，請使用[MSBuild 任務](../msbuild/msbuild-task.md)並將`Projects`參數設置為`$(MSBuildProjectFile)`。

使用`CallTarget`時，MSBuild 會評估新作用域中被調用的目標，而不是從中調用的相同範圍。 這意味著調用目標中的任何項和屬性更改對調用目標不可見。  要將資訊傳遞給調用目標，`TargetOutputs`請使用輸出參數。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

 下列範例會從 `CallOtherTargets` 的內部呼叫 `TargetA`。

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
- [目標](../msbuild/msbuild-targets.md)
