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
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747227"
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
|**Sources**|必要的 **ITaskItem[]** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)