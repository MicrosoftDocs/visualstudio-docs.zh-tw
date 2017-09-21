---
title: "IDebugMemoryBytes2::ReadAt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryBytes2::ReadAt"
helpviewer_keywords: 
  - "IDebugMemoryBytes2::ReadAt 方法"
  - "ReadAt 方法"
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

讀取的位元組序列，開始於指定的位置。  
  
## 語法  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```c#  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### 參數  
 `pStartContext`  
 \[in\][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件，指定要從何處開始讀取的位元組。  
  
 `dwCount`  
 \[in\]要讀取的位元組數目。  也會指定一段`rgbMemory`陣列。  
  
 `rgbMemory`  
 輸入 \[、 輸出\]填入的位元組陣列實際讀取的資料。  
  
 `pdwRead`  
 \[\] out傳回實際讀取的連續位元組數目。  
  
 `pdwUnreadable`  
 輸入 \[、 輸出\]傳回 \[無法讀取的位元組數目。  如果用戶端不願就無法讀取的位元組數目，則可能是 null 值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 如果要求 100 個位元組和第一個 50 是否已可讀、 後 20 則無法讀取，而其餘的 30 容易閱讀，這個方法會傳回：  
  
 \*`pdwRead` \= 50  
  
 \*`pdwUnreadable` \= 20  
  
 如此一來，因為`*pdwRead + *pdwUnreadable < dwCount`，呼叫端必須進行讀取的原始要求的 100 剩餘的 30 個位元組的其他呼叫，並[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)物件傳入的`pStartContext`參數必須前移 70。  
  
## 請參閱  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)