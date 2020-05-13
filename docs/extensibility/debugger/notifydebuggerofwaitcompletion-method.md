---
title: 通知調試等待完成方法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NotifyDebuggerOfWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: 841c5908-4f3f-400b-a7b0-96a95f362817
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8963e29a067754c0e8c89b9db336b239ac682ce1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738341"
---
# <a name="notifydebuggerofwaitcompletion-method"></a>通知除錯等待完成方法
占位符方法用作調試器的斷點目標。 此方法不能內聯或優化。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

## <a name="syntax"></a>語法

```vb
private void NotifyDebuggerOfWaitCompletion()
```

## <a name="remarks"></a>備註
 如果設置了具有任務的調試器通知位,則所有具有任務的聯接操作都應調用此方法。

## <a name="requirements"></a>需求

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
