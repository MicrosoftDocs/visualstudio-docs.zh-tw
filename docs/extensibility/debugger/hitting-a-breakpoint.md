---
title: 叫用中斷點 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1286af8222703028d5a8a1bd2dbb0d990ca7e30c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889901"
---
# <a name="hit-a-breakpoint"></a>叫用中斷點
當偵錯引擎 (DE) 執行，或逐步執行時叫用中斷點時下, 一節會說明的程序：

## <a name="troubleshoot-a-hit-breakpoint"></a>疑難排解點擊的中斷點

1. DE 傳送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)介面做**EVENT_SYNC_STOP**。

2. 工作階段的偵錯管理員 (SDM) 會呼叫[IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)取得已點擊的中斷點。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)