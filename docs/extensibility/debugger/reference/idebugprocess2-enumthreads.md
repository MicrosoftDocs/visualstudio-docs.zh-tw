---
title: "IDebugProcess2::EnumThreads | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::EnumThreads"
helpviewer_keywords: 
  - "IDebugProcess2::EnumThreads"
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取處理序中執行的所有執行緒的清單。  
  
## 語法  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### 參數  
 `ppEnum`  
 \[\] out傳回[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)物件，其中包含一份程序中的所有程式中的所有執行緒。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會列舉每個程式中執行的執行緒，然後將控制項結合成一個處理程序的檢視執行緒。  單一執行緒可能會執行多個程式。 這個方法會列舉該執行緒一次。  
  
 這個方法會顯示一份不重複的處理序的執行緒。  否則，如果您要列舉特定程式上執行的執行緒，使用[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)方法。  
  
## 請參閱  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)