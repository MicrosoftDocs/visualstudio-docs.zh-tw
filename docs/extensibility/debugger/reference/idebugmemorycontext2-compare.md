---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare 方法"
  - "Compare 方法"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

比較記憶體內容，以指示的比較旗標，傳回的比對的第一個內容索引的方式來指定陣列中每一種情形。  
  
## 語法  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### 參數  
 `compare`  
 \[in\]介於[CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)列舉型別，決定執行的比較類型。  
  
 `rgpMemoryContextSet`  
 \[in\]若要參考的陣列[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)要比較的物件。  
  
 `dwMemoryContextSetLen`  
 \[in\]內容中的數字`rgpMemoryContextSet`陣列。  
  
 `pdwMemoryContext`  
 \[\] out會傳回滿足比較的第一個記憶體內容的索引。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  傳回`E_COMPARE_CANNOT_COMPARE`如果無法比較兩個內容。  
  
## 備註  
 偵錯引擎 \(DE\) 並沒有支援所有類型的比較作業，但是它必須至少都支援`CONTEXT_EQUAL`， `CONTEXT_LESS_THAN`， `CONTEXT_GREATER_THAN`和`CONTEXT_SAME_SCOPE`。  
  
## 請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)