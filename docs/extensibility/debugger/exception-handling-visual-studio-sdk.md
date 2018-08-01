---
title: 例外狀況處理 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab3a3aafdca83305b86ce083e53e654b637cf110
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232061"
---
# <a name="exception-handling-visual-studio-sdk"></a>例外狀況處理 (Visual Studio SDK)
以下說明擲回例外狀況時，就會發生的程序。  
  
## <a name="exception-handling-process"></a>例外狀況處理程序  
  
1.  當第一次擲回例外狀況，但它由正在進行偵錯的程式中例外狀況處理常式之前，偵錯引擎 (DE) 會將傳送[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)為停止事件工作階段偵錯管理員 (SDM)。 `IDebugExceptionEvent2`只有例外狀況 （在偵錯封裝中的 [例外狀況] 對話方塊中指定） 的設定可讓您指定使用者想要停止 first-chance 例外狀況通知會傳送。  
  
2.  SDM 呼叫[IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)取得例外狀況的屬性。  
  
3.  偵錯封裝呼叫[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)來判斷什麼選項，以呈現給使用者。  
  
4.  偵錯封裝會要求使用者如何開啟 first-chance 例外狀況對話方塊處理的例外狀況。  
  
5.  如果使用者選擇繼續，會呼叫 SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。  
  
    -   如果此方法會傳回 s_ok 時，會呼叫[IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。  
  
         -或-  
  
         如果此方法會傳回 S_FALSE，該程式進行偵錯獲得第二個機會處理例外狀況。  
  
6.  如果正在偵錯程式會有第二個可能發生例外狀況處理常式，就會傳送 DE`IDebugExceptionEvent2`來為 SDM **EVENT_SYNC_STOP**。  
  
7.  偵錯封裝會要求使用者如何開啟 first-chance 例外狀況對話方塊處理的例外狀況。  
  
8.  偵錯封裝呼叫[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)來判斷什麼選項，以呈現給使用者。  
  
9. 偵錯封裝會要求使用者如何開啟第二個可能發生的例外狀況對話方塊處理的例外狀況。  
  
10. 如果此方法會傳回 s_ok 時，會呼叫`IDebugExceptionEvent2::PassToDebuggee`。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)