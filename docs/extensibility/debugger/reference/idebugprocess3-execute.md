---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

會繼續執行此程序，從停止的狀態。  清除任何先前的執行狀態 \(例如，一個步驟中\) 時，程序啟動時執行一次。  
  
> [!NOTE]
>  應該使用這個方法，而不是[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)。  
  
## 語法  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### 參數  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示要執行的執行緒。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當使用者開始執行，從停止的狀態，在某些其他處理序的執行緒時，在此程序上呼叫這個方法。  當使用者選取，也會呼叫這個方法**開始** 指令從 **偵錯**在 IDE 中的功能表。  這個方法的實作可能會像電話一樣簡單[繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)程序中目前的執行緒上的方法。  
  
> [!WARNING]
>  不要傳送停止事件或立即 \(同步\) 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [繼續](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)