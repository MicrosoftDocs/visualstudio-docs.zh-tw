---
title: TASK_STATE_WAITING_ON_CHILDREN 欄位 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae7f7930161b07dc8aeb4f3ff8bfb506e9f6e737
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345399"
---
# <a name="taskstatewaitingonchildren-field"></a>TASK_STATE_WAITING_ON_CHILDREN 欄位
工作已完成執行其委派，並在暗中等候附加的子工作完成。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 (CIL)。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位會包含此值，請<xref:System.Threading.Tasks.Task.Status%2A>屬性會傳回<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)