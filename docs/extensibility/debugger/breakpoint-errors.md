---
title: 斷點錯誤 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739225"
---
# <a name="breakpoint-errors"></a>斷點錯誤
當斷點嘗試綁定到代碼但失敗時,下面描述了該過程。

## <a name="troubleshoot-a-breakpoint-error"></a>排除斷點錯誤

1. 除錯引擎 (DE) 向工作階段除錯管理員 (SDM) 傳送[IDebugBreakpointErrorEvent2。](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)

2. SDM 調用[IDebugBreakpointErrorEvent2::獲取錯誤斷點](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)(IDebugErrorBreakpoint2+)`ppErrorBP`以獲取錯誤斷點。

3. SDM 調用[IDebugError 斷點2::獲取待定斷點](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)以獲取錯誤斷點源自的掛起斷點。

4. SDM 調用[IDebugErrorBreakpoint2::獲取斷點解析](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md),以獲取有關錯誤斷點未能綁定的原因。

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
