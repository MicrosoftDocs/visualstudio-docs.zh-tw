---
title: Message 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865358"
---
# <a name="message-task"></a>Message 工作

在建置期間記錄訊息。

## <a name="parameters"></a>參數

 下表說明 `Message` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`Importance`|選擇性的 `String` 參數。<br /><br /> 指定訊息的重要性。 此參數的值可以是 `high`、`normal` 或 `low`。 預設值是 `normal`。|
|`Text`|選擇性的 `String` 參數。<br /><br /> 要記錄的錯誤文字。|

## <a name="remarks"></a>備註

 該`Message`任務允許 MSBuild 專案在生成過程中的不同步驟向記錄器發送消息。

 如果 `Condition` 參數評估為 `true`，將會記錄 `Text` 參數的值，而建置將會繼續執行。 如果 `Condition` 參數不存在，便會記錄訊息文字。 如需有關記錄的詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

 預設情況下，消息將發送到所有已註冊的記錄器。 記錄器會解譯 `Importance` 參數。 通常，當記錄器詳細性`high`設置為<xref:Microsoft.Build.Framework.LoggerVerbosity>時，將發送設置為 的消息集。`Minimal` 。 當記錄器詳細性`low`設置為<xref:Microsoft.Build.Framework.LoggerVerbosity>時，將發送一條消息集。`Detailed`.

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="example"></a>範例

 下列程式碼範例會將訊息記錄到所有已註冊的記錄器。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>另請參閱

- [任務引用](../msbuild/msbuild-task-reference.md)
- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
