---
title: "例外狀況處理 (Visual Studio SDK) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4a0d950de8e9f91232e3526064561a7508c133b4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>例外狀況處理 (Visual Studio SDK)
以下描述擲回例外狀況時，就會發生的程序。  
  
## <a name="exception-handling-process"></a>例外狀況處理程序  
  
1.  當第一次擲回例外狀況，但它由程式偵錯時的例外狀況處理常式之前，偵錯引擎 (DE) 會將傳送[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)為停止事件工作階段偵錯管理員 (SDM)。 `IDebugExceptionEvent2`只有例外狀況 （例外狀況 對話方塊中偵錯封裝中指定） 的設定會指定使用者想要停止在發生第一個例外狀況的通知會傳送。  
  
2.  SDM 呼叫[IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)取得例外狀況的屬性。  
  
3.  偵錯封裝呼叫[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)來判斷哪些選項來呈現給使用者。  
  
4.  偵錯封裝詢問使用者如何開啟 first-chance 例外狀況對話方塊中處理例外狀況。  
  
5.  如果使用者選擇繼續，會呼叫 SDM [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)。  
  
    -   如果這個方法會傳回 S_OK 時，會呼叫[IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)。  
  
         -或-  
  
         如果此方法會傳回 S_FALSE，程式進行偵錯獲得第二個機會處理此例外狀況。  
  
6.  如果正在偵錯的程式有沒有第二個可能的例外狀況處理常式，就會傳送 DE`IDebugExceptionEvent2`來做為 SDM **EVENT_SYNC_STOP**。  
  
7.  偵錯封裝詢問使用者如何開啟 first-chance 例外狀況對話方塊中處理例外狀況。  
  
8.  偵錯封裝呼叫[IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)來判斷哪些選項來呈現給使用者。  
  
9. 偵錯封裝詢問使用者如何開啟第二個出現的例外狀況對話方塊中處理例外狀況。  
  
10. 如果這個方法會傳回 S_OK 時，會呼叫`IDebugExceptionEvent2::PassToDebuggee`。  
  
## <a name="see-also"></a>另請參閱  
 [呼叫偵錯工具事件](../../extensibility/debugger/calling-debugger-events.md)