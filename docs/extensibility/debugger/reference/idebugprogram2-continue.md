---
title: "IDebugProgram2::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

會繼續執行此程式從停止的狀態。  要保留任何先前的執行狀態 \(例如，一個步驟中\)，程式即開始執行一次。  
  
> [!NOTE]
>  這個方法已被取代。  請改用 [繼續](../../../extensibility/debugger/reference/idebugprocess3-continue.md) 方法。  
  
## 語法  
  
```cpp#  
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
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)表示執行緒的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 在這個程式，不論多少程式正在進行偵錯，哪一個程式所產生的停止事件，會呼叫這個方法。  實作必須保留先前的執行狀態 \(例如，一個步驟中\)，且繼續執行，就好像它永遠不會已停止之前完成之前執行。  也就是說，如果此程式中的執行緒正在執行 「 進入 」 作業，已停止，因為其他程式停止，而且會呼叫這個方法後再程式必須先完成進入函式 9。  
  
> [!WARNING]
>  不要傳送停止事件或立即 \(同步\) 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)