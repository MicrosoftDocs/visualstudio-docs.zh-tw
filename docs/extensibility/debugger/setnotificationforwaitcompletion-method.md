---
title: 設定通知等待完成方法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712866"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion 方法
設置或清除TASK_STATE_WAIT_COMPLETION_NOTIFICATION狀態位。

 **命名空間:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **程式集**:mscorlib(在*mscorlib.dll*中)

## <a name="syntax"></a>語法

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>參數
 `enabled`

 `true`設置位;`false`取消設置位。

## <a name="exceptions"></a>例外狀況

## <a name="remarks"></a>備註
 除錯器設定此位以説明退出非同步方法體。 如果是`enabled``true`,只能對尚未完成的任務調用此方法。 何時`enabled``false`,可以在已完成的任務上調用此方法。 在這兩個事件中,它只能用於承諾樣式的任務。

## <a name="requirements"></a>需求

## <a name="see-also"></a>另請參閱
- [工作類別](../../extensibility/debugger/task-class-internal-members.md)
