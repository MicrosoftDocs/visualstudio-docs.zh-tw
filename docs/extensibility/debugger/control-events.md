---
title: "控制事件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3220e3c6ef1a20b8a434fbfab13b419beb331032
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="control-events"></a>控制項事件
您必須控制您的程式執行期間傳送事件。 所有事件都會傳送使用[IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md)介面，並具有需要您實作的屬性[IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md)方法。  
  
## <a name="additional-methods"></a>其他方法  
 某些事件需要進行其他方法，實作如下：  
  
-   傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)介面初始化偵錯引擎 (DE) 時需要您實作[IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)方法。  
  
-   執行控制項都必須實作這類控制項事件中當做[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)和[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面。 **IDebugBreakEvent2**只有需要非同步符號。  
  
-   逐步執行函式需要有實作[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面和其方法。  
  
 衍生自中斷點的事件都需要實作[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)， [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)，和[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)介面，並將[IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)和[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)方法。  
  
 非同步的運算式評估會要求您實作[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)介面及其[IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[和 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)方法。  
  
 同步事件都需要實作[IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法。  
  
 針對您要寫入輸出字串樣式的引擎，您必須執行[IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)