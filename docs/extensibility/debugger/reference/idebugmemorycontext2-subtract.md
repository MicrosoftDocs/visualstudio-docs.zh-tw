---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "減去方法"
  - "IDebugMemoryContext2::Subtract 方法"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

減去指定的值，從目前的內容，並傳回新的內容。  
  
## 語法  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### 參數  
 `dwCount`  
 \[in\]以遞減的記憶體位元組數目。  
  
 `ppMemCxt`  
 \[\] out傳回新的[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 記憶體內容是地址，所以減去一個地址產生新的地址，需要新的內容介面。  
  
 這個方法必須產生新的內容，即使產生地址超出此內容相關聯的記憶體空間。  唯一的例外是如果無記憶體可配置新的內容，或是`ppMemCxt`為 null 值 \(也就是錯誤\)。  
  
## 請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)