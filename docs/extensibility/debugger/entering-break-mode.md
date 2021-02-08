---
title: 進入中斷模式 |Microsoft Docs
description: 瞭解函式中發生的中斷點所發生的程式、在游標處執行至原始程式碼的行，或執行至中斷點。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3ec09994f6998f87daafc690b1908b31e54706b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840648"
---
# <a name="enter-break-mode"></a>進入中斷模式
下列資訊描述在逐步執行函式之後遇到中斷點時所發生的程式，執行至具有游標所在的源程式碼，或執行至中斷點。

## <a name="break-mode-process"></a>中斷模式進程

1. Debug engine (DE) 傳送 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)、 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)或任何其他停止事件，使 IDE 進入中斷模式。

2. SDM 會從執行緒取得呼叫堆疊資訊，如下所示：

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2：： GetDocumentCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 以取得原始程式碼資訊

    - [IDebugDocumentCoNtext2：： GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) 以取得檔案名

    - [IDebugDocumentCoNtext2：： GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 可取得語句範圍

    - [IDebugStackFrame2：： GetCodeCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 可取得記憶體資訊

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
