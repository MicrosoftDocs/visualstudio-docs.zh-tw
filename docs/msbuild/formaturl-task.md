---
title: FormatUrl 工作 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fcd4ed0c60d615f0c213e1af5099c5e94a9b485
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634119"
---
# <a name="formaturl-task"></a>FormatUrl 工作

將 URL 轉換為正確的 URL 格式。

## <a name="parameters"></a>參數

 下表說明 `FormatUrl` 工作的參數。

|參數|描述|
|---------------|-----------------|
|`InputUrl`|選擇性的 `String` 參數。<br /><br /> 指定要格式化的 URL。|
|`OutputUrl`|選擇性的 `String` 輸出參數。<br /><br /> 指定已格式化 URL。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 有關這些附加參數及其說明的清單，請參閱[任務擴展基類](../msbuild/taskextension-base-class.md)。

## <a name="see-also"></a>另請參閱

- [工作](../msbuild/msbuild-tasks.md)
- [任務引用](../msbuild/msbuild-task-reference.md)