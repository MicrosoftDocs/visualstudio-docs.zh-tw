---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObject 方法"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立使用建構函式的物件。  
  
## 語法  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### 參數  
 `pConstructor`  
 \[in\][IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件，表示要建立物件的建構函式。  
  
 `dwArgs`  
 \[in\]中的參數數目 `pArg`陣列。  表示傳遞至建構函式的參數數目。  
  
 `pArg`  
 \[in\]陣列的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件代表參數傳遞至建構函式。  
  
 `ppObject`  
 \[\] out傳回`IDebugObject`代表剛建立的物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法來建立物件，表示一個類別 \(或其他需要建構函式的複雜型別\) 的執行個體也就是該參數用於函式由[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  
  
 如果物件參數不需要建構函式，呼叫[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)方法。  
  
## 請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)