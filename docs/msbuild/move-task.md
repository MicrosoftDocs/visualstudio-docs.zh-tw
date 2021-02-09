---
title: Move 工作 | Microsoft Docs
description: 深入瞭解 MSBuild Move 工作的參數和設定，這會將檔案移到新位置。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9121c14037ac1bc5740d1f0684f92226a361e6d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918188"
---
# <a name="move-task"></a>Move 工作

將檔案移到新位置。

## <a name="parameters"></a>參數

 下表說明 `Move` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`DestinationFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 指定要將來源檔案移動到其中的檔案清單。 這份清單預期會是一對一對應 `SourceFiles` 參數中指定的清單。 亦即，`SourceFiles` 中指定的第一個檔案會移動到 `DestinationFiles` 中指定的第一個位置，依此類推。|
|`DestinationFolder`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定要將檔案移動至其中的目錄。|
|`MovedFiles`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 輸出參數。<br /><br /> 包含已成功移動的項目。|
|`OverwriteReadOnlyFiles`|選擇性的 `Boolean` 參數。<br /><br /> 如果為 `true`，即使已標示為唯讀檔案，還是會覆寫這些檔案。|
|`SourceFiles`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定要移動的檔案。|

## <a name="remarks"></a>備註

 您必須指定 `DestinationFolder` 或 `DestinationFiles` 參數，但不能同時指定這兩者。 如果同時指定這兩者，工作即會失敗，並記錄錯誤。

 `Move` 工作會針對所需的目的地檔案建立所需的資料夾。

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
