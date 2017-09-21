---
title: "IEnumDebugFields::Next | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Next"
helpviewer_keywords: 
  - "IEnumDebugFields::Next 方法"
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回下一組項目，從列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### 參數  
 `celt`  
 \[in\]若要擷取的項目數。  也會指定最大`rgelt`陣列。  
  
 `rgelt`  
 輸入 \[、 輸出\]陣列的[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)會自動填入的項目。  
  
 `pceltFetched`  
 \[\] out傳回以實際傳回的項目數`rgelt`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果少於無法傳回所要求的項目數目。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)