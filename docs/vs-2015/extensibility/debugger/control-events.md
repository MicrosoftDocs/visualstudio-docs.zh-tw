---
title: 控制事件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4073da9036e11f90fbf7202095e70fce797ea015
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414629"
---
# <a name="control-events"></a>控制項事件
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

您必須在受控制的程式執行期間傳送事件。 所有事件都是使用 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 介面傳送，而且具有需要您執行 [IDebugEvent2：： GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方法的屬性。  
  
## <a name="additional-methods"></a>其他方法  
 某些事件需要執行其他方法，如下所示：  
  
- 當 debug engine (DE) 初始化時，傳送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面需要您執行 [IDebugEngineCreateEvent2：： GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 方法。  
  
- 執行控制項需要將這類控制項事件實作為 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 和[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面。 只有非同步中斷才需要**IDebugBreakEvent2** 。  
  
- 逐步執行函式需要 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面和其方法的實作為。  
  
  衍生自中斷點的事件需要實 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 介面，以及 [IDebugBreakpointBoundEvent2：： GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法。  
  
  非同步運算式評估需要您執行 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面及其 [IDebugExpressionEvaluationCompleteEvent2：： system.componentmodel.design.serialization.codedomserializerbase.getexpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[和 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 方法。  
  
  同步事件需要執行 [IDebugEngine2：： ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 方法。  
  
  若要讓引擎撰寫字串樣式輸出，您必須執行 [IDebugOutputStringEvent2：： GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) 方法。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
