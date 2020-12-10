---
title: TaskScheduler 類別-內部成員 |Microsoft Docs
description: 深入瞭解可協助您執行自訂偵錯工具之 TaskScheduler 類別的內部成員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10528e57137f8605e7f140d4ab8d4a3399029a5f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996002"
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
