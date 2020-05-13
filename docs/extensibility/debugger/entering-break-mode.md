---
title: 進入中斷模式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bbcec8adf6468f70d95df5f291ce1e5540406cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738886"
---
# <a name="enter-break-mode"></a>進入中斷模式
以下資訊描述在踏入函數、運行到具有游標的原始程式碼行或運行到斷點後遇到斷點時發生的過程。

## <a name="break-mode-process"></a>中斷模式程序

1. 除錯引擎 (DE) 傳送[IDebugBreakpointEvent2、IDebugexceptionEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)或任何其他停止事件,導致 IDE 進入中斷模式。 [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)

2. SDM 從線程獲取調用堆疊資訊,如下所示:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2::取得文檔上下文](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)取得原始碼資訊

    - [IDebugDocumentContext2::取得名稱](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)獲取檔案名稱

    - [IDebugDocumentContext2::取得敘述範圍](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)以取得敘述範圍

    - [IDebugStackFrame2::取得代碼上下文](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)獲取記憶體資訊

## <a name="see-also"></a>另請參閱
- [呼叫除錯器事件](../../extensibility/debugger/calling-debugger-events.md)
