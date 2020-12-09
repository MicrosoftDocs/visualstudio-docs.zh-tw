---
title: 控制事件 |Microsoft Docs
description: 瞭解如何使用 IDebugEvent2 介面，在受控制的程式執行期間傳送事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf7f59384d9317e4be173c93b6165d754a35ad8f
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914240"
---
# <a name="control-events"></a>控制事件
您必須在受控制的程式執行期間傳送事件。 所有事件都是使用 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) 介面傳送，而且具有需要您執行 [IDebugEvent2：： GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) 方法的屬性。

## <a name="additional-methods"></a>其他方法
 某些事件需要執行其他方法，如下所示：

- 當 debug engine (DE) 初始化時，傳送 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面需要您執行 [IDebugEngineCreateEvent2：： GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) 方法。

- 執行控制項需要將這類控制項事件實作為 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) 和[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面。 只有非同步中斷才需要 **IDebugBreakEvent2** 。

- 逐步執行函式需要 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面和其方法的實作為。

  衍生自中斷點的事件需要實 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)和 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 介面，以及 [IDebugBreakpointBoundEvent2：： GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法。

  非同步運算式評估需要您執行 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) 介面及其 [IDebugExpressionEvaluationCompleteEvent2：： system.componentmodel.design.serialization.codedomserializerbase.getexpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[和 GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) 方法。

  同步事件需要執行 [IDebugEngine2：： ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) 方法。

  若要讓引擎撰寫字串樣式輸出，您必須執行 [IDebugOutputStringEvent2：： GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) 方法。

## <a name="see-also"></a>另請參閱
- [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
