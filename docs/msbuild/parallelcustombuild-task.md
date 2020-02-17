---
title: ParallelCustomBuild 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279260"
---
# <a name="parallelcustombuild-task"></a>ParallelCustomBuild 工作

執行 [CustomBuild 工作](../msbuild/custombuild-task.md)的平行執行個體。

## <a name="parameters"></a>參數

下表說明 **ParallelCustomBuild** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**BreakOnFirstFailure**|選擇性的 **bool** 參數。|
|**MaxItemsInBatch**|選擇性的 **int** 參數。|
|**MaxProcesses**|選擇性的 **int** 參數。|
|**來源**|必要的 **ITaskItem[]** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)