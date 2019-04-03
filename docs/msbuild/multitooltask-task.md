---
title: MultiToolTask 工作 | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.multitooltask
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), MultiToolTask task
- MultiToolTask task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: a16a61c06bf80bef3fbb78f155cd8b41905a8d72
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515177"
---
# <a name="multitooltask-task"></a>MultiToolTask 工作

沒有描述。

## <a name="parameters"></a>參數

下表說明 **MultiToolTask** 工作的參數。

|參數|說明|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|選擇性的 **string[]** 參數。|
|**SemaphoreProcCount**|選擇性的 **string** 參數。|
|**SchedulerFunction**|選擇性的 **string** 參數。|
|**SchedulerVerbose**|選擇性的 **bool** 參數。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**TaskAssemblyName**|選擇性的 **string** 參數。|
|**TaskName**|必要的 **string** 參數。|
|**TrackerLogDirectory**|必要的 **string** 參數。|

## <a name="see-also"></a>另請參閱

[工作參考](../msbuild/msbuild-task-reference.md)