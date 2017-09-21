---
title: "IDebugMemoryContext2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetName"
helpviewer_keywords: 
  - "IDebugMemoryContext2::GetName 方法"
  - "GetName 方法"
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取此內容的使用者可顯示的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(  
   out string pbstrName  
);  
```  
  
#### 參數  
 `pbstrName`  
 \[\] out傳回的記憶體內容的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 通常不使用的記憶體內容的名稱。  
  
## 請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)