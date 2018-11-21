---
title: 例外狀況處理 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2640641a4cb02c34255cbd0b0016c31a0dd14638
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732964"
---
# <a name="exception-handling-visual-studio-sdk"></a>例外狀況處理 (Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

