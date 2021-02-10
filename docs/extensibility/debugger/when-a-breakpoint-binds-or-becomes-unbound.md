---
title: 當中斷點系結或變成未系結時 |Microsoft Docs
description: 瞭解未系結的中斷點。 當呼叫完成時，中斷點無法系結時，中斷點的系結時間和建立時間會有所不同。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97ac7dc9afbd3b740c95a7e76a30836e938eaeaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99968498"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>當中斷點系結或變成未系結時
當呼叫 [IDebugPendingBreakpoint2：： CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) 方法時無法系結中斷點時，中斷點的系結時間和建立時間會有所不同。

## <a name="methods-called"></a>呼叫的方法
 會話 debug manager (SDM) 會呼叫下列方法：

1. [IDebugEngine2：： CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。 DE 會傳回 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)。

2. [IDebugPendingBreakpoint2：： Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)。

3. [IDebugPendingBreakpoint2：：虛擬化](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)。

4. [IDebugPendingBreakpoint2：： Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)方法，並傳回 S_OK。 DE 會傳送 [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) 或 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)。

5. [IDebugBreakpointBoundEvent2：： GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) 和 [IDebugBreakpointBoundEvent2：： EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) 方法，以驗證並取得系結的中斷點。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
