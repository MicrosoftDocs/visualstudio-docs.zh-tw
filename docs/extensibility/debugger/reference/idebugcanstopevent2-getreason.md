---
description: 取得 debug engine (DE) 要停止的原因。
title: IDebugCanStopEvent2：： GetReason |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2125bb90693d5a4c5cc23ac1225d56dea636de2e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085048"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
取得 debug engine (DE) 要停止的原因。

## <a name="syntax"></a>語法

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>參數
`pcr`\
擴展傳回 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 列舉中的值，這個值會描述這個事件的原因。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 通常會在 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 方法之前呼叫這個方法，讓呼叫端可以決定是否要將非零的 (`TRUE`) 傳遞給 `IDebugCanStopEvent2::CanStop` 方法。

 停止的原因可能是，也 `CANSTOP_ENTRYPOINT` 就是 de 已到達進入點，或者 `CANSTOP_STEPIN` ，這表示已將 de 帶到函數中。

## <a name="see-also"></a>另請參閱
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
