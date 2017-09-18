---
title: "IDebugProcess3::Step | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

會導致處理程序逐步執行一個指令或陳述式。  
  
> [!NOTE]
>  應該使用這個方法，而不是[逐步執行](../../../extensibility/debugger/reference/idebugprogram2-step.md)。  
  
## 語法  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### 參數  
 `pThread`  
 \[in\][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，代表正在螞蟻的執行緒。  
  
 `sk`  
 \[in\]其中[STEPKIND](../../../extensibility/debugger/reference/stepkind.md)的值。  
  
 `step`  
 \[in\]其中[STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)的值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則會傳回錯誤碼。  
  
## 備註  
 如果有任何的執行緒同步處理或執行緒之間的通訊，當在逐步執行特定的執行緒時，就應該會執行其他處理序中的執行緒。  
  
 **警告**不會停止事件或即時的 \(同步\) 事件，以傳送[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)時處理這個呼叫。 否則偵錯工具可能會停止回應。  
  
## 請參閱  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)