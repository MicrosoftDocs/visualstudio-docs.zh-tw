---
description: 這個介面代表已準備好系結至程式碼位置的中斷點。
title: IDebugPendingBreakpoint2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 05e66a0066abca5fb657960f2042b738a10e59ca
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169726"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
這個介面代表已準備好系結至程式碼位置的中斷點。

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 在它支援中斷點的過程中，執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 的呼叫會從 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) 介面建立暫止中斷點。 系結的[](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)呼叫會 `IDebugBreakpoint2` 在程式中建立表示系結中斷點的介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPendingBreakpoint2` 。

|方法|描述|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|判斷此暫止中斷點是否可以系結至程式碼位置。|
|[綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將這個暫止中斷點系結至一個或多個程式碼位置。|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得這個暫止中斷點的狀態。|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立這個暫止中斷點的中斷點要求。|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切換此暫止中斷點的虛擬化狀態。|
|[啟用](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換此暫止中斷點的啟用狀態。|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設定或變更與此暫止中斷點相關聯的條件。|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設定或變更與此暫止中斷點相關聯的傳遞計數。|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉從此暫止中斷點系結的所有中斷點。|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉由此暫止中斷點產生的所有錯誤中斷點。|
|[刪除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除這個暫止中斷點及其系結的所有中斷點。|

## <a name="remarks"></a>備註
 `IDebugPendingBreakpoint2` 可以視為將中斷點系結至可套用至一或多個程式之程式碼所需的所有必要資訊的提供者。

 暫止的中斷點可能會產生一個以上的系結中斷點。 例如，c + + 樣式範本中的中斷點可能會針對該範本的每個唯一實例產生系結中斷點。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
