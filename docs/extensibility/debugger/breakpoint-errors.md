---
title: 中斷點錯誤 |Microsoft Docs
description: 瞭解中斷點嘗試系結至程式碼但失敗時的程式，以及如何針對中斷點錯誤進行疑難排解。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 840fde5943cb2249bdf73cc92ca15878ae4e3890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943450"
---
# <a name="breakpoint-errors"></a>中斷點錯誤
以下說明中斷點嘗試系結至程式碼但失敗時的進程。

## <a name="troubleshoot-a-breakpoint-error"></a>針對中斷點錯誤進行疑難排解

1. Debug engine (DE) 會將 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) 傳送至會話 debug MANAGER (SDM) 。

2. SDM 會呼叫 [IDebugBreakpointErrorEvent2：： GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP`) 以取得錯誤中斷點。

3. SDM 會呼叫 [IDebugErrorBreakpoint2：： GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) ，以取得產生錯誤中斷點的暫止中斷點。

4. SDM 會呼叫 [IDebugErrorBreakpoint2：： GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) ，以取得錯誤中斷點無法系結的原因。

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
