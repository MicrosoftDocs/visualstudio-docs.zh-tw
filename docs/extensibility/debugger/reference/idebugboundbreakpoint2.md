---
title: IDebug邊界斷點2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735418"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
此介面表示綁定到代碼位置的斷點。

## <a name="syntax"></a>語法

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。

## <a name="notes-for-callers"></a>通話備註
 對[Bind 的](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)呼叫將創建此介面。 對[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)和[Next 的](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)調用也可以獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBoundBreakpoint2`。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|獲取創建指定邊界斷點的掛起斷點。|
|[取得狀態](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|獲取此綁定斷點的狀態。|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|獲取此綁定斷點的當前命中計數。|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|獲取描述此斷點的斷點解析度。|
|[啟用](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或禁用斷點。|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|設置此綁定斷點的命中計數。|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設置或更改與此綁定斷點關聯的條件。|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|設置或更改與此綁定斷點關聯的傳遞計數。|
|[刪除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除中斷點。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
