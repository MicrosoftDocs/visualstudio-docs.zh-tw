---
title: 控制事件 |微軟文件
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
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739095"
---
# <a name="control-events"></a>控制事件
您必須在程式的受控執行期間發送事件。 所有事件都使用[IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md)介面發送,並且具有需要您實現[IDebugEvent2::getAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md)方法的屬性。

## <a name="additional-methods"></a>其他方法
 某些事件需要實現其他方法,如下所示:

- 當調試引擎 (DE) 初始化時,發送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)介面需要實現[IDebugEngineCreateEvent2:getEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)方法。

- 執行控制需要實現[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)和[IDebugStepcompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面等控制事件。 **IDebugBreakEvent2**僅適用於非同步中斷。

- 進入函數需要實現[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面及其方法。

  從斷點派生的事件需要實現[IDebugBreakpointErrorEvent2、IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)和[IDebugBreakpoint事件2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)介面,以及[IDebugBreakpointBoundEvent2:取得掛起的斷點](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)點和[EnumBoundBreakpoint 方法](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)。 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)

  非同步運算要求您實現[IDebugExpression 表示式評估完成事件2 介面](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)及其[IDebugExpression 運算式評估完成事件2::獲取表達式](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[和 getResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)方法。

  同步事件需要實現[IDebugEngine2::繼續從同步事件](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)方法。

  要編寫字串樣式輸出,必須實現[IDebugStringEvent2::getString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)方法。

## <a name="see-also"></a>另請參閱
- [執行控制及狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)
