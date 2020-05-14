---
title: TASK_STATE_CANCELED欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712752"
---
# <a name="task_state_canceled-field"></a>TASK_STATE_CANCELED欄位
任務在到達運行狀態之前已取消,或者它確認其取消並無一例外地完成。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在 mscorlib.dll 中)

 由於您無法從 .NET 框架訪問此內部成員,因此在通用中間語言 (CIL) 中提供了以下語法。

## <a name="syntax"></a>語法

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>備註
 如果[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)欄位包含此值<xref:System.Threading.Tasks.Task.Status%2A>,則屬性<xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>將傳回 。

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
