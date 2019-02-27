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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6594620051675f2c0ce6e06ca098d26e443f624b
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617232"
---
# <a name="calltarget-task"></a>CallTarget 工作
叫用專案檔內指定的目標。

## <a name="task-parameters"></a>工作參數
 下表說明 `CallTarget` 工作的參數。


| 參數 | 說明 |
|---------------------------| - |
| `RunEachTargetSeparately` | 選擇性 `Boolean` 輸入參數。<br /><br /> 如果為 `true`，每個目標會呼叫一次 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎。 如果為 `false`，會呼叫一次 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎以建置所有目標。 預設值為 `false`。 |
| `TargetOutputs` | 選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含所有建置目標的輸出。 |
| `Targets` | 選擇性的 `String[]` 參數。<br /><br /> 指定要建置的一或多個目標。 |
| `UseResultsCache` | 選擇性的 `Boolean` 參數。<br /><br /> 如果是 `true`，即傳回快取的結果 (如果有的話)。<br /><br /> **注意**：執行 MSBuild 工作時，會在範圍 (ProjectFileName, GlobalProperties)[TargetNames] 內快取它的結果，當作組建項目清單。 |

## <a name="remarks"></a>備註
 如果在 `Targets` 中指定的目標失敗，而 `RunEachTargetSeparately` 是 `true`，則工作會繼續建置其餘的目標。

 如果您想要建置預設目標，請使用 [MSBuild 工作](../msbuild/msbuild-task.md)，並設定 `Projects` 參數等於 `$(MSBuildProjectFile)`。

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些其他參數的清單及其描述，請參閱 [TaskExtension 基底類別](../msbuild/taskextension-base-class.md)。

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
- [工作參考](../msbuild/msbuild-task-reference.md)
- [目標](../msbuild/msbuild-targets.md)