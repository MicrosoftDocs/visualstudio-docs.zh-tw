---
title: MultiToolTask 工作 | Microsoft Docs
description: 存取描述 MSBuild MultiToolTask 工作之必要參數和選擇性參數的資料表。
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6d76aa3762b254ee35ada1e4e81fe857f509a4e5
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048969"
---
# <a name="multitooltask-task"></a>MultiToolTask 工作

沒有描述。

## <a name="parameters"></a>參數

下表說明 **MultiToolTask** 工作的參數。

|參數|描述|
|---------------|-----------------|
|**EnvironmentVariablesToSet**|選擇性的 **string []** 參數。|
|**SemaphoreProcCount**|選擇性的 **字串** 參數。|
|**SchedulerFunction**|選擇性的 **字串** 參數。|
|**SchedulerVerbose**|選擇性的 **bool** 參數。|
|**來源**|必要的 **ITaskItem []** 參數。|
|**TaskAssemblyName**|選擇性的 **字串** 參數。|
|**TaskName**|必要的 **字串** 參數。|
|**TrackerLogDirectory**|必要的 **字串** 參數。|

## <a name="see-also"></a>請參閱

[工作參考](../msbuild/msbuild-task-reference.md)
