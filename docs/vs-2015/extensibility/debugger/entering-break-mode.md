---
title: 進入中斷模式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182257"
---
# <a name="entering-break-mode"></a>進入中斷模式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

以下說明在逐步執行函式、執行至具有資料指標的源程式碼，或執行至中斷點的程式程式碼之後，遇到中斷點時發生的進程。  
  
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
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)
