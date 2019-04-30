---
title: GetTaskSchedulersForDebugger 方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5df6dc3147a92f14d6858a82a6d997442dec30b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925650"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
擷取的所有陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>傳回值
 所有陣列<xref:System.Threading.Tasks.TaskScheduler>且目前正在使用中的物件<xref:System.AppDomain>。

## <a name="remarks"></a>備註
 這個方法不是安全執行緒，以及您不應該使用它與其他執行個體同時<xref:System.Threading.Tasks.TaskScheduler>。 只在偵錯工具已暫止的其他所有執行緒時，請從 偵錯工具呼叫此方法。

## <a name="see-also"></a>另請參閱
- [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)