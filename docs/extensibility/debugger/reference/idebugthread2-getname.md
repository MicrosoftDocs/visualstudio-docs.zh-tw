---
title: "IDebugThread2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetName"
helpviewer_keywords: 
  - "IDebugThread2::GetName"
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得執行緒的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName (   
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回執行緒的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 擷取的名稱永遠是一個可顯示的名稱，這個名稱所說明的執行緒。  執行緒名稱可能從一種執行階段架構支援名為執行緒，或可能是衍生自偵錯引擎的名稱。  此外，設定執行緒的名稱，呼叫[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)方法。  
  
## 請參閱  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)