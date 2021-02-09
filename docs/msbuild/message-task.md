---
title: Message 工作 | Microsoft Docs
description: 深入瞭解 MSBuild Message 工作的參數和設定，這會在組建期間記錄訊息。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb2a1837210a5f36577d3bf677a4152033914f49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918243"
---
# <a name="message-task"></a>Message 工作

在建置期間記錄訊息。

## <a name="parameters"></a>參數

 下表說明 `Message` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`Importance`|選擇性的 `String` 參數。<br /><br /> 指定訊息的重要性。 此參數的值可以是 `high`、`normal` 或 `low`。 預設值是 `normal`。|
|`Text`|選擇性的 `String` 參數。<br /><br /> 要記錄的錯誤文字。|

## <a name="remarks"></a>備註

 此工作 `Message` 可讓 MSBuild 專案在組建程式中的不同步驟發出訊息給記錄器。

 如果 `Condition` 參數評估為 `true`，將會記錄 `Text` 參數的值，而建置將會繼續執行。 如果 `Condition` 參數不存在，便會記錄訊息文字。 如需有關記錄的詳細資訊，請參閱[取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)。

 根據預設，訊息會傳送至所有已註冊的記錄器。 記錄器會解譯 `Importance` 參數。 一般來說， `high` 當記錄器詳細資訊設定為時，會傳送的訊息設定為 <xref:Microsoft.Build.Framework.LoggerVerbosity> 。`Minimal` 。 `low`當記錄器詳細資訊設定為時，會傳送的訊息設 <xref:Microsoft.Build.Framework.LoggerVerbosity> 為。 `Detailed`

 除了上述所列的參數，此項工作還會繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別中的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

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

- [工作參考](../msbuild/msbuild-task-reference.md)
- [取得組建記錄檔](../msbuild/obtaining-build-logs-with-msbuild.md)
