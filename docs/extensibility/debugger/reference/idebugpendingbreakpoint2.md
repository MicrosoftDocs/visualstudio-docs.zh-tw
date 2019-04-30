---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 816fad53554675e7f29cef838d4ea24e154dca8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871930"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
此介面表示中斷點已繫結至程式碼位置。

## <a name="syntax"></a>語法

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)會建立從暫止中斷點[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面。 呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)建立`IDebugBreakpoint2`介面，表示在程式中的繫結的中斷點。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPendingBreakpoint2`。

|方法|描述|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|判斷這個暫止中斷點可以繫結到程式碼的位置。|
|[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將這個暫止中斷點繫結至一個或多個程式碼位置。|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得這個暫止中斷點的狀態。|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立這個暫止中斷點的中斷點要求。|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切換虛擬化的狀態這暫止的中斷點。|
|[Enable](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換這個暫止中斷點的啟用的狀態。|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設定或變更相關聯與這個暫止中斷點的條件。|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設定或變更與這個暫止的中斷點相關聯的傳遞計數。|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉所有繫結從這個暫止中斷點的中斷點。|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉導致這個暫止中斷點的所有錯誤中斷點。|
|[刪除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除這個暫止中斷點和繫結從它的所有中斷點。|

## <a name="remarks"></a>備註
 `IDebugPendingBreakpoint2` 可以視為將中斷點繫結至可套用至一或多個程式的程式碼所需的所有必要資訊的提供者。

 暫止中斷點可能會產生一個以上的繫結的中斷點。 例如，在中斷點C++-樣式範本可能會產生每個唯一的執行個體，該範本的繫結的中斷點。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)