---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf7b693c058cd69ab2dcb79be787cf5a16d8f8a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864019"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 類別-內部成員
這篇文章描述的內部成員<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類別可協助您實作自訂的偵錯工具。 如需此類別的一般資訊，請參閱<xref:System.Threading.Tasks.TaskScheduler>參考文章。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|擷取所有排定工作的陣列。|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|擷取的所有陣列<xref:System.Threading.Tasks.TaskScheduler>目前使用中的物件。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [適用於.NET Framework 的平行擴充內部資訊](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)