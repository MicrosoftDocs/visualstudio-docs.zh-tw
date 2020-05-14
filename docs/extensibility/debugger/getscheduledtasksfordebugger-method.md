---
title: 取得除錯器方法的預定工作 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738658"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger 方法
檢索所有計劃任務的陣列。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>傳回值
 所有計劃任務的陣列。 每個任務正在執行或已完成執行。

## <a name="remarks"></a>備註
 此方法不安全,不應將其與其他實例同時使用<xref:System.Threading.Tasks.TaskScheduler>。 僅當調試器掛起所有其他線程時,才從調試器調用此方法。

## <a name="see-also"></a>另請參閱
- [工作計劃器類](../../extensibility/debugger/taskscheduler-class-internal-members.md)
