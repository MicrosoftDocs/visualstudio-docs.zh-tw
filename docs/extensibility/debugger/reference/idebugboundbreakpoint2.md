---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20dbd4ca3f5c56d8519bc6dbfbe362f7904ae56d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350111"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
這個介面表示繫結至程式碼位置的中斷點。

## <a name="syntax"></a>語法

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)會建立此介面。 若要呼叫[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)並[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)也可以取得此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBoundBreakpoint2`。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得從中建立指定的繫結的中斷點暫止中斷點。|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得這個繫結中斷點的狀態。|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|取得此繫結中斷點目前叫用的次數。|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述此中斷點的中斷點解析。|
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|設定此繫結中斷點的叫用的次數。|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設定或變更與此繫結中斷點相關聯的條件。|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|設定或變更與此繫結中斷點相關聯的傳遞計數。|
|[刪除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除中斷點。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)