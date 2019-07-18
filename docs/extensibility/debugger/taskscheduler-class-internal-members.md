---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 865e12819a5e7325886c0f7f5d8425a6b3d2e393
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331337"
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