---
title: Breakpoint-Related 方法 |Microsoft Docs
description: Visual Studio 的偵錯工具支援系結的中斷點，其已成功系結至程式碼中的位置，而暫止的中斷點尚未系結。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9472f1ff4105790951ddd687d7e71c3e57fa39da
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914461"
---
# <a name="breakpoint-related-methods"></a>中斷點相關的方法
Debug engine (DE) 必須支援中斷點的設定。 Visual Studio 的偵錯工具支援下列類型的中斷點：

- Bound

     透過 UI 要求並成功系結至指定的程式碼位置

- Pending

     透過 UI 要求，但尚未系結至實際指示

## <a name="discussion"></a>討論
 例如，當指令尚未載入時，就會發生暫止中斷點。 載入程式碼時，暫止中斷點會嘗試系結至指定位置的程式碼，也就是在程式碼中插入 break 指令。 事件會傳送至會話 debug manager (SDM) 以表示成功系結，或通知有系結錯誤。

 暫止中斷點也會管理它自己的對應系結中斷點的內部清單。 一個暫止的中斷點可能會導致在程式碼中插入許多中斷點。 Visual Studio 的偵錯工具 UI 會顯示暫止中斷點及其對應的系結中斷點的樹狀檢視。

 建立和使用暫止中斷點需要實 [IDebugEngine2：： CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 方法以及下列 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) 介面方法。

|方法|描述|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|判斷指定的暫止中斷點是否可以系結至程式碼位置。|
|[綁定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將指定的暫止中斷點系結至一個或多個程式碼位置。|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得暫止中斷點的狀態。|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立暫止中斷點的中斷點要求。|
|[啟用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換暫止中斷點的啟用狀態。|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉從暫止中斷點系結的所有中斷點。|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉暫止中斷點所產生的所有錯誤中斷點。|
|[刪除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除暫止中斷點及其系結的所有中斷點。|

 若要列舉系結中斷點和錯誤中斷點，您必須執行 [IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) 和 [IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)的所有方法。

 系結至程式碼位置的暫止中斷點必須執行下列 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) 方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得包含中斷點的暫止中斷點。|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得系結中斷點的狀態。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述中斷點的中斷點解析度。|
|[啟用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|
|[刪除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除系結的中斷點。|

 解析和要求資訊需要執行下列 [IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md) 方法。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|取得解析度所表示之中斷點的型別。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|取得描述中斷點的中斷點解析資訊。|

 在系結期間可能發生的錯誤解決需要執行下列 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) 方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得包含錯誤中斷點的暫止中斷點。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤中斷點的中斷點錯誤解決方法。|

 在系結期間可能會發生之錯誤的解決方式，也需要下列 [IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|取得中斷點的型別。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|取得中斷點的解析資訊。|

 若要在中斷點處查看原始程式碼，您必須執行 [IDebugStackFrame2：： GetDocumentCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 和/或 [IDebugStackFrame2：： GetCodeCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)方法。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
