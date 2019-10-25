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
- MSBuild (C++), MultiToolTask task
- MultiToolTask task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 137fb53a46c3fa31a69602906ef53d2f65e25c4b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747239"
---
# <a name="multitooltask-task"></a>MultiToolTask 工作

沒有描述。

## <a name="parameters"></a>參數

下表說明 **MultiToolTask** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|選擇性的 **string[]** 參數。|
|**SemaphoreProcCount**|選擇性的 **string** 參數。|
|**SchedulerFunction**|選擇性的 **string** 參數。|
|**SchedulerVerbose**|選擇性的 **bool** 參數。|
|**Sources**|必要的 **ITaskItem[]** 參數。|
|**TaskAssemblyName**|選擇性的 **string** 參數。|
|**TaskName**|必要的 **string** 參數。|
|**TrackerLogDirectory**|必要的 **string** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)