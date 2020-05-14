---
title: 當斷點綁定或變為未綁定 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712337"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>當斷點繫結或變為未綁定時
當在對[IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)方法進行調用時無法綁定斷點時,斷點的綁定時間和創建時間是不同的。

## <a name="methods-called"></a>呼叫的方法
 工作階段除錯管理員 (SDM) 呼叫以下方法:

1. [IDebugEngine2::建立掛起的斷點](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。 DE 傳回[IDebug 掛起的斷點2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)。

2. [IDebug 掛起斷點2::啟用](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)。

3. [IDebug 掛起斷點2::虛擬化](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)。

4. [IDebugPendingBreakpoint2::綁定](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)方法並返回S_OK。 DE 傳送[IDebugBreakpoint 繫結事件2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)或[IDebugBreakpoint 錯誤事件2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)。

5. [IDebugBreakpoint綁定事件2::獲取待定斷點](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)和[IDebugBreakpoint綁定事件2::enumBoundBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)方法以驗證和獲取綁定的斷點。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
