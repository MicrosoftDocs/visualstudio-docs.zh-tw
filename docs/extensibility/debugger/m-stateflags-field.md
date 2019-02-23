---
title: m_stateFlags 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6766fa98d6141005ed88d623ef8608035593a2a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704588"
---
# <a name="mstateflags-field"></a>m_stateFlags 欄位
儲存的目前狀態的相關資訊<xref:System.Threading.Tasks.Task>物件。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>備註
 您通常會使用<xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName>屬性來存取這個值。

 這個成員可以是下列值的任何組合：

-   [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

-   [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

-   [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

-   [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

-   [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)