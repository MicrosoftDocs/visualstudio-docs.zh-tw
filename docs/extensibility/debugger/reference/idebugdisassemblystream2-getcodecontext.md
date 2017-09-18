---
title: "IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetCodeContext"
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDisassemblyStream2::GetCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

傳回指定的程式碼的位置識別碼相對應的程式碼內容物件。  
  
## 語法  
  
```cpp#  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```c#  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### 參數  
 `uCodeLocationId`  
 \[in\]指定的程式碼的位置識別碼。  請參閱 \[備註\] 部份的[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)的程式碼的位置識別碼說明的方法。  
  
 `ppCodeContext`  
 \[\] out傳回[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)物件，表示相關聯的程式碼內容。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 可以從呼叫傳回的程式碼的位置識別碼[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)方法，而且可以出現在[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。  
  
 若要將程式碼內容轉換成程式碼的位置識別碼時，呼叫[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)方法。  
  
## 請參閱  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)   
 [GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)