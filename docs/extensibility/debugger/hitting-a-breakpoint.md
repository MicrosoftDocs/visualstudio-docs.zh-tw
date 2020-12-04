---
title: 觸達中斷點 |Microsoft Docs
description: 本文說明當 debug engine 在執行或逐步執行時叫用中斷點時，所發生的程式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560846"
---
# <a name="hit-a-breakpoint"></a>叫用中斷點
下一節描述當 debug engine (DE) 在執行或逐步執行時叫用中斷點時的程式：

## <a name="troubleshoot-a-hit-breakpoint"></a>針對點擊中斷點進行疑難排解

1. 「取消」會將 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 介面傳送成 **EVENT_SYNC_STOP**。

2. 會話 debug manager (SDM) 呼叫 [IDebugBreakpointEvent2：：： EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 來取得點擊的中斷點。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
