---
title: 斷點相關方法 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72ec63e500ac86a4a5bd66a2956fe0fb06c8834
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739204"
---
# <a name="breakpoint-related-methods"></a>與斷點相關的方法
調試引擎 (DE) 必須支援斷點設置。 Visual Studio 除錯支援以下類型的斷點:

- Bound

     透過 UI 要求並成功結合到指定的程式碼位置

- Pending

     透過 UI 請求但尚未綁定到實際說明

## <a name="discussion"></a>討論區
 例如,當指令尚未載入時,將發生掛起的斷點。 載入代碼時,掛起的斷點嘗試綁定到指定位置的代碼,即在代碼中插入中斷指令。 事件將發送到工作階段除錯管理員 (SDM), 以指示成功的綁定或通知存在綁定錯誤。

 掛起的斷點還管理其自己的相應綁定斷點的內部清單。 一個掛起的斷點可能導致在代碼中插入許多斷點。 Visual Studio 調試 UI 顯示掛起斷點的樹視圖及其相應的綁定斷點。

 創建和使用掛起的斷點需要實現[IDebugEngine2:::creatependingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法以及[以下 IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面的方法。

|方法|描述|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|確定指定的掛起斷點是否可以綁定到代碼位置。|
|[綁定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將指定的掛起斷點綁定到一個或多個代碼位置。|
|[取得狀態](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|獲取掛起斷點的狀態。|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|獲取用於創建掛起斷點的斷點請求。|
|[啟用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換掛起斷點的啟用狀態。|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|枚舉從掛起的斷點綁定的所有斷點。|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|枚舉來自掛起斷點的所有錯誤斷點。|
|[刪除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除掛起的斷點和所有斷點。|

 要枚舉綁定斷點和錯誤斷點,必須實現[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)和[IEnum DebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)的所有方法。

 綁定到代碼位置的掛起斷點需要實現以下[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|獲取包含斷點的掛起斷點。|
|[取得狀態](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|獲取綁定斷點的狀態。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|獲取描述斷點的斷點解析度。|
|[啟用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或禁用斷點。|
|[刪除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除綁定斷點。|

 解析和請求資訊需要實現以下[IDebugBreakpoint決議2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|獲取由解析度表示的斷點的類型。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|獲取描述斷點的斷點解析度資訊。|

 解決綁定期間可能發生的錯誤需要實現以下[IDebugErrorBreakpointpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|獲取包含錯誤斷點的掛起斷點。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|獲取描述錯誤斷點的斷點錯誤解析度。|

 解決繫結期間可能發生的錯誤還需要以下方法的[IDebugErrorBreakpoint 決議2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|獲取斷點的類型。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|獲取斷點的解析度資訊。|

 在斷點處查看原始程式碼需要實現[IDebugStackFrame2:::獲取文檔上下文](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)和/或[IDebugStackFrame2:::獲取代碼上下文](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)的方法。

## <a name="see-also"></a>另請參閱
- [執行控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
