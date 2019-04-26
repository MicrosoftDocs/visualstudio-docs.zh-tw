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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963906"
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