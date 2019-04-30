---
title: 中斷點相關的方法 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1781e6aab84bfcdc665ef0d779130decc9c6421
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926020"
---
# <a name="breakpoint-related-methods"></a>中斷點相關的方法
偵錯引擎 (DE) 必須支援的設定中斷點。 Visual Studio 偵錯支援下列類型的中斷點：

- 繫結

     透過 UI 要求及成功繫結到指定的程式碼的位置

- 擱置

     透過 UI，但無法尚未繫結至實際的指示要求

## <a name="discussion"></a>討論
 比方說，指示尚未載入時，就會發生暫止中斷點。 程式碼載入時，暫止的中斷點試，也就是繫結至指定位置的程式碼，以中斷指令插入程式碼中。 事件會傳送工作階段的偵錯管理員 (SDM)，以指出成功的繫結，或通知已繫結錯誤。

 暫止中斷點也會管理它自己內部的相對應的繫結中斷點清單。 一個暫止中斷點可能會導致許多中斷點的插入動作，在程式碼。 Visual Studio 偵錯 UI 顯示暫止中斷點的樹狀結構檢視和其對應的繫結中斷點。

 建立和使用暫止中斷點需要實作[IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法，以及下列的方法[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。

|方法|描述|
|------------|-----------------|
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|判斷指定暫止的中斷點可以繫結到程式碼的位置。|
|[Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|繫結指定暫止的中斷點至一或多個程式碼位置。|
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得暫止中斷點的狀態。|
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立暫止中斷點的中斷點要求。|
|[Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換暫止中斷點的啟用的狀態。|
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉所有的中斷點暫止中斷點的資料繫結。|
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉所有錯誤中斷點所產生的暫止中斷點。|
|[刪除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除暫止中斷點和繫結從它的所有中斷點。|

 若要列舉的繫結的中斷點和錯誤的中斷點，您必須實作的所有方法[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)以及[IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)。

 暫止繫結至程式碼的中斷點位置需要實作下列[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得包含中斷點暫止中斷點。|
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得繫結中斷點的狀態。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述中斷點的中斷點解析。|
|[Enable](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|
|[刪除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除繫結的中斷點。|

 解析和要求資訊需要實作下列[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|取得中斷點表示所解析的型別。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|取得描述中斷點的中斷點解析資訊。|

 在繫結期間可能發生之錯誤的解析所需的下列實作[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)方法。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得包含錯誤的中斷點暫止中斷點。|
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤中斷點的中斷點錯誤解決方式。|

 在繫結期間可能發生之錯誤的解決方法也會需要的下列方法[IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|取得中斷點的型別。|
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|取得中斷點解析資訊。|

 檢視在中斷點的原始程式碼會要求您實作的方法[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)及 （或) 的方法[IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)