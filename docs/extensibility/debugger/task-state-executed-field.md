---
title: TASK_STATE_EXECUTED欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa637b8bc29f53ca6dde1b13310d83a5e176408f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712705"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED欄位
工作正在執行，但尚未完成。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在 mscorlib.dll 中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值<xref:System.Threading.Tasks.Task.Status%2A>,則屬性<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>將傳回 。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
