---
title: "IDebugReference2::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugReference2::GetMemoryContext"
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得參考的記憶體內容。  保留供將來使用。  
  
## 語法  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```c#  
int GetMemoryContext (   
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### 參數  
 `ppMemory`  
 \[\] out傳回[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，代表的參照值相關聯的記憶體。  
  
## 傳回值  
 永遠傳回 `E_NOTIMPL`。  
  
## 請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)