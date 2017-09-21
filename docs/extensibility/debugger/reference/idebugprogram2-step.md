---
title: "IDebugProgram2::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

執行一個步驟。  
  
> [!NOTE]
>  這個方法已被取代。  請改用 [逐步執行](../../../extensibility/debugger/reference/idebugprocess3-step.md) 方法。  
  
## 語法  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### 參數  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表正在螞蟻的執行緒。  
  
 `sk`  
 \[in\]介於[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)指定的步驟類型的列舉型別。  
  
 `step`  
 \[in\]介於[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) \(例如，藉由陳述式或指令\) 中指定的單位是步驟的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 如果有任何的執行緒同步處理或執行緒之間的通訊，當在逐步執行特定的執行緒時，就應該會執行其他程式中的執行緒。  
  
> [!WARNING]
>  不要傳送停止事件或立即 \(同步\) 事件[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)