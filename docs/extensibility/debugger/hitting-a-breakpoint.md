---
title: 擊中斷點 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738574"
---
# <a name="hit-a-breakpoint"></a>叫用中斷點
以下部分介紹除錯引擎 (DE) 在執行或步進時遇到斷點的過程:

## <a name="troubleshoot-a-hit-breakpoint"></a>排除命中斷點故障

1. DE 將[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面作為**EVENT_SYNC_STOP**發送。

2. 會話調試管理器 (SDM) 調用[IDebugBreakpointEvent2:::enumBreakpoint](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)獲取命中的斷點。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
