---
title: TASK_STATE_RAN_TO_COMPLETION欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4a898ff09ff45ae77da91e54ba22351e9f70978d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712617"
---
# <a name="task_state_ran_to_completion-field"></a>TASK_STATE_RAN_TO_COMPLETION欄位
工作已成功完成執行。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值<xref:System.Threading.Tasks.Task.Status%2A>,則屬性<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>將傳回 。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
