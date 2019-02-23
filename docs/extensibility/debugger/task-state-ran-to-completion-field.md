---
title: TASK_STATE_RAN_TO_COMPLETION 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2bfec03e44b4af46ed75761d96f1e37bc1370e0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704900"
---
# <a name="taskstaterantocompletion-field"></a>TASK_STATE_RAN_TO_COMPLETION 欄位
工作已成功完成執行。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位會包含此值，請<xref:System.Threading.Tasks.Task.Status%2A>屬性會傳回<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)