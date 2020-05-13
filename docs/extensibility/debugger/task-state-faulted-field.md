---
title: TASK_STATE_FAULTED欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c9bd5b9ec57e652dd7a57ee3434a2525eeeedbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712683"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED欄位
工作因未處理的例外狀況而完成。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值<xref:System.Threading.Tasks.Task.Status%2A>,則屬性<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>將傳回 。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
