---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳送偵錯事件的告知。  
  
## 語法  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### 參數  
 `pEngine`  
 \[in\][IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)物件，代表正在傳送這個事件的偵錯引擎 \(DE\)。  將 DE 才能填寫這個參數。  
  
 `pProcess`  
 \[in\][IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)物件，表示發生該事件的處理程序。  這個參數會填入由工作階段偵錯管理員 \(SDM\)。  將 DE 總是會傳遞 null 值，這個參數。  
  
 `pProgram`  
 \[in\][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)物件，表示發生此事件的程式。  對於大部分的事件，此參數不是 null 值。  
  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示發生此事件的執行緒。  停止事件，這個參數不能堆疊框架取自此參數為 null 值。  
  
 `pEvent`  
 \[in\][IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)表示偵錯事件的物件。  
  
 `riidEvent`  
 \[in\]識別從取得哪些事件介面的 GUID `pEvent`參數。  
  
 `dwAttrib`  
 \[in\]從的旗標組合[EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當呼叫這個方法中， `dwAttrib`參數必須符合傳回的值[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)方法的事件物件，稱為傳入的`pEvent`參數。  
  
 不論事件本身是否是非同步以非同步的方式，公佈偵錯的所有事件。  當將 DE 呼叫這個方法時，傳回的值並不表示是否已處理事件，只在接收到的事件是否。  事實上，在大部分的情況下，事件尚未處理這個方法傳回時。  
  
## 請參閱  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)