---
title: "IDebugStackFrame3::InterceptCurrentException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
helpviewer_keywords: 
  - "IDebugStackFrame3::InterceptCurrentException"
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

在要攔截目前例外狀況時呼叫目前的堆疊框架上的偵錯工具。  
  
## 語法  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```c#  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### 參數  
 `dwFlags`  
 \[in\]請指定不同的動作。  目前，只有[INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)值`IEA_INTERCEPT`支援，必須指定。  
  
 `pqwCookie`  
 \[\] out用來識別特定的例外狀況的唯一值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
 以下是最常見的錯誤傳回。  
  
|錯誤|描述|  
|--------|--------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|目前的例外狀況不被攔截。|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|尚未處理常式尚未搜尋目前的執行框架。|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|這個方法不支援此框架中。|  
  
## 備註  
 擲回例外狀況時，偵錯工具會取得控制項從索引鍵的時間點的執行階段期間處理程序的例外狀況。  在這些索引鍵的時間，偵錯工具可以要求目前的堆疊框架框架是否要攔截的例外狀況。  如此一來，被攔截的例外狀況會是基本上堆疊框架中，上飛例外處理常式，即使該堆疊框架不會有例外處理常式 \(例如，在程式碼中的 try\/catch 區塊\)。  
  
 當偵錯工具想要知道是否應該攔截的例外狀況時，它會在目前的堆疊框架物件上呼叫這個方法。  這個方法會負責處理的例外狀況的所有詳細資料。  如果[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)並未實作介面或`InterceptStackException`方法會傳回任何錯誤，然後偵錯工具會繼續正常處理例外狀況。  
  
> [!NOTE]
>  例外狀況可以攔截只能在 managed 程式碼，也就是當程式的偵錯下執行。NET 執行階段。  協力廠商語言實作人員可實作不用多說， `InterceptStackException`在它們自己所選擇的偵錯引擎。  
  
 攔截完畢後[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)信號。  
  
## 請參閱  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT\_EXCEPTION\_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)