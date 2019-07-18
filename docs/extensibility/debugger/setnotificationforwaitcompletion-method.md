---
title: SetNotificationForWaitCompletion 方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5d9bee2579cc3a93f657291551955f0c9b7565b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348588"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 方法
設定或清除 TASK_STATE_WAIT_COMPLETION_NOTIFICATION 狀態位元。

 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>

 **組件：** mscorlib (在*mscorlib.dll*)

## <a name="syntax"></a>語法

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>參數
 `enabled`

 `true` 若要設定的位元;`false`為未設定此位元。

## <a name="exceptions"></a>例外狀況

## <a name="remarks"></a>備註
 偵錯工具設定此位元，以協助從非同步方法主體中的步驟。 如果`enabled`是`true`，必須只能在尚未完成的工作上呼叫這個方法。 當`enabled`是`false`，可以在 已完成的工作上呼叫這個方法。 在可能情況下，它應該只用於承諾樣式工作。

## <a name="requirements"></a>需求

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)