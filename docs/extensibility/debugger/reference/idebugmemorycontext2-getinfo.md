---
title: "IDebugMemoryContext2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetInfo"
helpviewer_keywords: 
  - "GetInfo 方法"
  - "IDebugMemoryContext2::GetInfo 方法"
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取[CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)結構描述內容。  
  
## 語法  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### 參數  
 `dwFields`  
 \[in\]從的旗標組合[CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)列舉型別，會指出哪一個欄位的[CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)結構有要填滿。  
  
 `pInfo`  
 輸入 \[、 輸出\]`CONTEXT_INFO`將被填入的結構。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)