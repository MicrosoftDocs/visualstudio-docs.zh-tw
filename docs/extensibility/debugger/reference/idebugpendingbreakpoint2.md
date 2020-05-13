---
title: IDebug 待定斷點2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725647"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
此介面表示準備綁定到代碼位置的斷點。

## <a name="syntax"></a>語法

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。

## <a name="notes-for-callers"></a>通話備註
 對[創建掛起斷點的](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)調用從[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面創建一個掛起的斷點。 對[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)的`IDebugBreakpoint2`呼叫將建立表示程式中的綁定斷點的介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPendingBreakpoint2`。

|方法|描述|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|確定此掛起的斷點是否可以綁定到代碼位置。|
|[綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將此掛起的斷點綁定到一個或多個代碼位置。|
|[取得狀態](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|獲取此掛起斷點的狀態。|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|獲取用於創建此掛起斷點的斷點請求。|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切換此掛起斷點的虛擬化狀態。|
|[啟用](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換此掛起斷點的啟用狀態。|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設置或更改與此掛起的斷點關聯的條件。|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設置或更改與此掛起的斷點關聯的傳遞計數。|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|枚舉從此掛起的斷點綁定的所有斷點。|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|枚舉此掛起斷點產生的所有錯誤斷點。|
|[刪除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除此掛起的斷點和所有從其綁定的斷點。|

## <a name="remarks"></a>備註
 `IDebugPendingBreakpoint2`可以認為是綁定斷點到可應用於一個或多個程式的代碼所需的所有資訊的提供者。

 掛起的斷點可能會生成多個綁定斷點。 例如,C++樣式範本中的斷點可以為該範本的每個唯一實例生成綁定斷點。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
