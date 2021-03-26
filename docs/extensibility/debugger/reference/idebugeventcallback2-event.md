---
description: 傳送 debug 事件的通知。
title: IDebugEventCallback2：： Event |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fec6984ffc30c3c368193079fdabc1752f63a65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065797"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
傳送 debug 事件的通知。

## <a name="syntax"></a>語法

```cpp
HRESULT Event( 
   IDebugEngine2*  pEngine,
   IDebugProcess2* pProcess,
   IDebugProgram2* pProgram,
   IDebugThread2*  pThread,
   IDebugEvent2*   pEvent,
   REFIID          riidEvent,
   DWORD           dwAttrib
);
```

```csharp
int Event( 
   IDebugEngine2  pEngine,
   IDebugProcess2 pProcess,
   IDebugProgram2 pProgram,
   IDebugThread2  pThread,
   IDebugEvent2   pEvent,
   ref Guid       riidEvent,
   uint           dwAttrib
);
```

## <a name="parameters"></a>參數
`pEngine`\
在 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 物件，表示正在傳送此事件 (DE) 的 debug engine。 填寫此參數必須有 DE。

`pProcess`\
在 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 物件，表示發生事件的進程。 會話 debug manager (SDM) 填入此參數。 DE 一律會為此參數傳遞 null 值。

`pProgram`\
在 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 物件，表示發生此事件的程式。 對於大部分的事件而言，這個參數不是 null 值。

`pThread`\
在代表發生這個事件之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。 若要停止事件，此參數不能是 null 值，因為堆疊框架是從此參數取得的。

`pEvent`\
在表示 debug 事件的 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 物件。

`riidEvent`\
在GUID，識別要從參數取得的事件介面 `pEvent` 。

`dwAttrib`\
在 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 列舉中的旗標組合。

## <a name="return-value"></a>傳回值
 如果成功，則傳回， `S_OK` 否則傳回錯誤碼。

## <a name="remarks"></a>備註
 呼叫這個方法時， `dwAttrib` 參數必須符合在參數中傳遞的事件物件上呼叫的 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方法所傳回的值 `pEvent` 。

 所有的 debug 事件都是以非同步方式張貼，不論事件本身是否為非同步。 當 DE 呼叫這個方法時，傳回值不會指出是否已處理事件，只會指出是否已收到事件。 事實上，在大部分情況下，此方法傳回時，事件尚未經過處理。

## <a name="see-also"></a>另請參閱
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
