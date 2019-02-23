---
title: IDebugBreakpointBoundEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 780c5ff6a8dcac69ed1aa99464269d58366f1f7e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706960"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
這個介面會告知工作階段的偵錯管理員 (SDM)，暫止中斷點具有已成功繫結至載入程式。

## <a name="syntax"></a>語法

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面做為其支援中斷點的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上 (使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面)。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 建立，並暫止中斷點已成功繫結至正在偵錯程式時，會傳送這個事件的物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，在 SDM 所提供的回呼函式。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointBoundEvent2`。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|取得與所繫結的暫止中斷點。|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|建立繫結此事件的中斷點的列舉值。|

## <a name="remarks"></a>備註
 每當中斷點繫結時，事件會傳送到 SDM。 如果中斷點無法繫結[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)傳送; 否則即為`IDebugBreakpointBoundEvent2`傳送。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)