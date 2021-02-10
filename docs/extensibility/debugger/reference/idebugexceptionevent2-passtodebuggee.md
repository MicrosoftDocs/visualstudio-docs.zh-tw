---
title: IDebugExceptionEvent2：:P assToDebuggee |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::PassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::PassToDebuggee
ms.assetid: a20d0f0b-2ca0-4437-bd22-9213c81d2738
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 03ce1499863197ed71ef38fcae6a256b1ca319a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933257"
---
# <a name="idebugexceptionevent2passtodebuggee"></a>IDebugExceptionEvent2::PassToDebuggee
指定是否應將例外狀況傳遞至執行繼續時所要進行的程式，或者是否應捨棄例外狀況。

## <a name="syntax"></a>語法

```cpp
HRESULT PassToDebuggee(
   BOOL fPass
);
```

```csharp
int PassToDebuggee(
   int fPass
);
```

## <a name="parameters"></a>參數
`fPass`\
在非零 (`TRUE`) 是否應將例外狀況傳遞給執行繼續時所要進行偵錯工具的程式; `FALSE` 如果應該捨棄例外狀況，則為零 () 。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法並不會實際導致正在進行偵錯工具的程式碼執行。 呼叫只是要設定下一個程式碼執行的狀態。 例如， [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) 方法的呼叫可能會 `S_OK` 隨 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)傳回。`dwState` 欄位設定為 `EXCEPTION_STOP_SECOND_CHANCE` 。

 IDE 可能會接收 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) 事件並呼叫 [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md) 方法。 如果未呼叫方法，debug engine (DE) 應該有預設行為來處理案例 `PassToDebuggee` 。

## <a name="see-also"></a>另請參閱
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)
- [繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)
