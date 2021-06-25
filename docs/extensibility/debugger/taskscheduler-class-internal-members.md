---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
description: 深入瞭解可協助您執行自訂偵錯工具之 TaskScheduler 類別的內部成員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900144"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler 類別-內部成員
本文說明 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> 可協助您執行自訂偵錯工具之類別的內部成員。 如需此類別的一般資訊，請參閱 <xref:System.Threading.Tasks.TaskScheduler> 參考文章。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取這些內部成員，所以會以一般中繼語言 () 的 CIL 來提供下列語法。

## <a name="syntax"></a>語法

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>成員

### <a name="methods"></a>方法

|名稱|描述|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|捕獲所有排程工作的陣列。|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|抓取目前作用中之所有物件的陣列 <xref:System.Threading.Tasks.TaskScheduler> 。|

## <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [.NET Framework 的平行延伸模組內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
