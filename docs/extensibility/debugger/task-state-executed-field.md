---
title: TASK_STATE_EXECUTED 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 551ac7af1e331f9c1e57b078be4924994ebe8a3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968550"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED 欄位
工作正在執行，但尚未完成。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** mscorlib.dll) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在) 的通用中繼語言中提供下列語法 (。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>備註
 如果 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 欄位包含此值，則 <xref:System.Threading.Tasks.Task.Status%2A> 屬性會傳回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> 。

## <a name="see-also"></a>另請參閱
- [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
