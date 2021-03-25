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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e093437fcc8b3e1e2663c2a46ebb3b70d32efbec
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059947"
---
# <a name="hit-a-breakpoint"></a>叫用中斷點
下一節描述當 debug engine (DE) 在執行或逐步執行時叫用中斷點時的程式：

## <a name="troubleshoot-a-hit-breakpoint"></a>針對點擊中斷點進行疑難排解

1. 「取消」會將 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 介面傳送成 **EVENT_SYNC_STOP**。

2. 會話 debug manager (SDM) 呼叫 [IDebugBreakpointEvent2：：： EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) 來取得點擊的中斷點。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
