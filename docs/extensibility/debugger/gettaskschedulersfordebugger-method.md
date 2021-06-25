---
description: 抓取目前作用中的所有 TaskScheduler 物件的陣列。
title: GetTaskSchedulersForDebugger 方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58cb913f5dbc729c297de8a34aa5dd4c3c99b48a
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900911"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
抓取目前作用中之所有物件的陣列 <xref:System.Threading.Tasks.TaskScheduler> 。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在) 的通用中繼語言中提供下列語法 (。

## <a name="syntax"></a>語法

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>傳回值
 <xref:System.Threading.Tasks.TaskScheduler>此中目前作用中之所有物件的陣列 <xref:System.AppDomain> 。

## <a name="remarks"></a>備註
 這個方法不是安全線程，因此您不應該與的其他實例同時使用它 <xref:System.Threading.Tasks.TaskScheduler> 。 只有當偵錯工具暫停所有其他執行緒時，才從偵錯工具呼叫這個方法。

## <a name="see-also"></a>另請參閱
- [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)
