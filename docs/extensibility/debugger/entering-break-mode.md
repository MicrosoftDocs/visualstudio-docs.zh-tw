---
title: 進入中斷模式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a57ec499941e8e07d93d1917b9d12f5dfd7aca79
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341568"
---
# <a name="enter-break-mode"></a>進入中斷模式
下列資訊說明逐步執行函式、 執行中，有資料指標的原始碼的行，或執行至中斷點之後遇到中斷點時所發生的程序。

## <a name="break-mode-process"></a>中斷模式處理序

1. 偵錯引擎 (DE) 會傳送[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)， [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)，或任何其他停止事件，讓 IDE 進入中斷模式。

2. 在 SDM 執行緒，從取得呼叫堆疊資訊的如下所示：

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)來取得來源的程式碼資訊

    - [IDebugDocumentContext2::GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)取得檔案名稱

    - [IDebugDocumentContext2::GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)取得陳述式範圍

    - [IDebugStackFrame2::GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)取得記憶體資訊

## <a name="see-also"></a>另請參閱
- [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)