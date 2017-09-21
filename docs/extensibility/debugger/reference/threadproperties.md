---
title: "THREADPROPERTIES | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADPROPERTIES"
helpviewer_keywords: 
  - "THREADPROPERTIES 結構"
ms.assetid: 7d397207-db03-4ec0-9f79-3794056ed89f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# THREADPROPERTIES
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

說明執行緒的屬性。  
  
## 語法  
  
```cpp#  
typedef struct _tagTHREADPROPERTIES {   
   THREADPROPERTY_FIELDS dwFields;  
   DWORD                 dwThreadId;  
   DWORD                 dwSuspendCount;  
   DWORD                 dwThreadState;  
   BSTR                  bstrPriority;  
   BSTR                  bstrName;  
   BSTR                  bstrLocation;  
} THREADPROPERTIES;  
```  
  
```c#  
public struct THREADPROPERTIES {   
   public uint   dwFields;  
   public uint   dwThreadId;  
   public uint   dwSuspendCount;  
   public uint   dwThreadState;  
   public string bstrPriority;  
   public string bstrName;  
   public string bstrLocation;  
};  
```  
  
## Members  
 dwFields  
 從的旗標組合[THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)描述此結構中的哪一個欄位都有效的列舉。  
  
 dwThreadId  
 執行緒識別碼。  
  
 dwSuspendCount  
 執行緒會暫停次數。  
  
 dwThreadState  
 介於[THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)表示作業的執行緒狀態列舉型別。  
  
 bstrPriority  
 字串，指定執行緒的優先順序。 比方說，"高於一般"、"標準"，或者"時間嚴重"。  
  
 bstName  
 執行緒名稱。  
  
 bstrLocation  
 執行緒位置 \(通常是最上層堆疊框架\)，通常會以目前停止執行方法的名稱。  
  
## 備註  
 這個結構會填入由呼叫[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)方法。  因此傳回的資訊通常用於填入**執行緒**視窗。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)