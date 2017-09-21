---
title: "IDebugProcess3::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

會繼續執行此程序，從停止的狀態。  要保留任何先前的執行狀態 \(例如，一個步驟中\)，並在處理序啟動執行一次。  
  
> [!NOTE]
>  應該使用這個方法，而不是[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。  
  
## 語法  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### 參數  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表若要繼續執行緒。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 在此程序，不論多少的處理程序正在進行偵錯，或哪個處理程序產生停止事件上呼叫這個方法。  實作必須保留先前的執行狀態 \(例如，一個步驟中\)，且繼續執行，就好像它永遠不會已停止之前完成之前執行。  也就是如果執行緒在這個程序在進入函式和已停止，因為其他處理序停止，然後再`Continue`呼叫，指定的執行緒必須先完成進入函式 9。  
  
 **警告**不會停止事件或即時的 \(同步\) 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)