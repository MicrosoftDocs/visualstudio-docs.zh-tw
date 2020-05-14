---
title: 取得任務計劃器除錯器方法 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3b0c8c16b10a4cf2268161d8a2db96c10303b1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738641"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger 方法
檢索當前處於活動狀態的所有<xref:System.Threading.Tasks.TaskScheduler>物件的陣列。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>傳回值
 當前在此<xref:System.AppDomain>處於活動狀態的所有<xref:System.Threading.Tasks.TaskScheduler>物件的陣列。

## <a name="remarks"></a>備註
 此方法不安全,不應將其與其他實例同時使用<xref:System.Threading.Tasks.TaskScheduler>。 僅當調試器掛起所有其他線程時,才從調試器調用此方法。

## <a name="see-also"></a>另請參閱
- [工作計劃器類](../../extensibility/debugger/taskscheduler-class-internal-members.md)
