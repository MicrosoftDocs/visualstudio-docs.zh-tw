---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateArrayObject 方法"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立陣列物件。  此陣列可以包含其中一個基本項目或物件執行個體的值。  
  
## 語法  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `ot`  
 \[in\]指定值，從[OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md)列舉型別，指出新的陣列物件的型別。  
  
 `pClassField`  
 \[in\][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表類別的物件，如果正在建立物件的陣列執行個體的值。  如果建立基本的物件陣列，這個參數會是 null 值。  
  
 `dwRank`  
 \[in\]陣序規範的陣列維度的數目。  
  
 `dwDims`  
 \[in\]陣列的每個維度的大小。  
  
 `dwLowBounds`  
 \[in\]每個維度的來源 \(通常是 0 或 1\)。  
  
 `ppObject`  
 \[\] out傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，表示新建立的陣列。  這實際上是[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法來建立物件，表示陣列參數至函式由其[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  
  
## 請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)