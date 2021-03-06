---
description: 工作已完成執行它的委派，並隱含地等候附加的子工作完成。
title: TASK_STATE_WAITING_ON_CHILDREN 欄位 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1533ef28b32450d9b039c27e49ba655dddfd6ebe
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223197"
---
# <a name="task_state_waiting_on_children-field"></a>TASK_STATE_WAITING_ON_CHILDREN 欄位
工作已完成執行它的委派，並隱含地等候附加的子工作完成。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在一般中繼語言 (的 CIL) 中提供下列語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>備註
 如果 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 欄位包含此值，則 <xref:System.Threading.Tasks.Task.Status%2A> 屬性會傳回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> 。

## <a name="see-also"></a>另請參閱
- [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
