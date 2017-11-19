---
title: "中斷點相關的方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint methods
- breakpoints, methods
ms.assetid: a6f77bf0-bf81-443f-8683-5f12075bbe10
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d743c98fd9e311f7f118c152e579178b07513d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="breakpoint-related-methods"></a>中斷點相關的方法
偵錯引擎 (DE) 必須支援的設定中斷點。 Visual Studio 偵錯支援下列類型的中斷點：  
  
-   繫結  
  
     透過 UI 要求，並成功繫結到指定的程式碼的位置  
  
-   擱置  
  
     要求透過 UI 但不是尚未繫結至實際的指示  
  
## <a name="discussion"></a>討論  
 例如，指示尚未載入時，就會發生暫止中斷點。 程式碼載入時，暫止中斷點嘗試繫結至程式碼中指定的位置，也就是，以插入的程式碼中斷的指示。 事件傳送至工作階段的偵錯管理員 (SDM) 表示成功的繫結，或是通知繫結錯誤。  
  
 暫止中斷點也會管理它自己的繫結的對應中斷點的內部清單。 一個暫止中斷點會造成許多中斷點插入的程式碼。 Visual Studio 偵錯 UI 顯示的樹狀檢視的暫止中斷點，和其對應的繫結中斷點。  
  
 建立和使用暫止中斷點需要實作[IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法，以及下列的方法[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  
  
|方法|說明|  
|------------|-----------------|  
|[CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|決定指定暫止中斷點可以繫結至程式碼位置。|  
|[繫結](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將繫結指定暫止中斷點到一或多個程式碼位置。|  
|[GetState](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得暫止中斷點的狀態。|  
|[GetBreakpointRequest](../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立暫止中斷點的中斷點要求。|  
|[啟用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換暫止中斷點的啟用的狀態。|  
|[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉從暫止中斷點繫結的所有中斷點。|  
|[EnumErrorBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉所有錯誤中斷點所導致的暫止中斷點。|  
|[刪除](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除暫止中斷點，並從其繫結的所有中斷點。|  
  
 若要列舉的繫結的中斷點和錯誤中斷點，您必須實作所有方法的[IEnumDebugBoundBreakpoints2](../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)和[IEnumDebugErrorBreakpoints2](../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)。  
  
 暫止繫結至程式碼的中斷點位置需要實作下列[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得包含中斷點暫止中斷點。|  
|[GetState](../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得繫結中斷點的狀態。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述中斷點的中斷點解析度。|  
|[啟用](../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|  
|[刪除](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除繫結的中斷點。|  
  
 解析度及要求資訊需要實作下列[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|取得中斷點解析度所代表的類型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|取得描述中斷點的中斷點解析資訊。|  
  
 在繫結期間可能發生之錯誤的解析所需的下列實作[IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得包含錯誤中斷點暫止中斷點。|  
|[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤中斷點的中斷點錯誤解決方式。|  
  
 在繫結期間可能發生之錯誤的解決方式也需要下列的方法[IDebugErrorBreakpointResolution2](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)。  
  
|方法|說明|  
|------------|-----------------|  
|[GetBreakpointType](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|取得中斷點類型。|  
|[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|取得中斷點的解決方法資訊。|  
  
 在中斷點處檢視原始碼需要您實作的方法[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)和 （或) 的方法[IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)