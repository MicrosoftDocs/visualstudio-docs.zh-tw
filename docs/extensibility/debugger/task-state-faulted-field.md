---
description: 工作因未處理的例外狀況而完成。
title: TASK_STATE_FAULTED 欄位 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5a8113f6145706d2863a4f0060a8627952eb0b3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223182"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED 欄位
工作因未處理的例外狀況而完成。

 **命名空間：** <xref:System.Threading.Tasks?displayProperty=fullName>

 **元件：** *mscorlib.dll*) 中的 mscorlib (

 因為您無法從 .NET Framework 存取此內部成員，所以會在一般中繼語言 (的 CIL) 中提供下列語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>備註
 如果 [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) 欄位包含此值，則 <xref:System.Threading.Tasks.Task.Status%2A> 屬性會傳回 <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> 。

## <a name="see-also"></a>另請參閱
- [Task 類別](../../extensibility/debugger/task-class-internal-members.md)
