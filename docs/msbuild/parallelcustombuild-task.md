---
title: ParallelCustomBuild 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 ParallelCustomBuild 工作來執行 CustomBuild 工作的平行實例。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048897"
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
|**來源**|必要的 **ITaskItem []** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)