---
title: "IDebugObject::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugObject::GetMemoryContext 方法"
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得表示物件的值的位址的記憶體內容。  
  
## 語法  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```c#  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### 參數  
 `pContext`  
 \[\] out傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，表示物件的值的位址。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 傳回的記憶體內容會指定值的位址，這表示[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件。  
  
## 請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)