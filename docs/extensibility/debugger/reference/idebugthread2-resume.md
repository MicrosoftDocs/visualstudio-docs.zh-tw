---
title: "IDebugThread2::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

繼續執行的執行緒。  
  
## 語法  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### 參數  
 `pdwSuspendCount`  
 \[\] out傳回恢復作業之後的暫停次數。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 每一個呼叫這個方法會暫停次數一直 0 到時，實際上會恢復執行。  這個暫停次數會顯示在**執行緒**偵錯\] 視窗。  
  
 每次呼叫這個方法，就必須要之前呼叫[暫止](../Topic/IDebugThread2::Suspend.md)方法。  暫停次數次數`IDebugThread2::Suspend`到目前為止已呼叫方法。  
  
## 請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [暫止](../Topic/IDebugThread2::Suspend.md)