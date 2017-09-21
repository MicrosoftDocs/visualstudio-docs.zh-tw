---
title: "IDebugFunctionObject::CreateObjectNoConstructor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreateObjectNoConstructor 方法"
ms.assetid: 4e2bd6d5-f4bd-4c10-a998-3db451c9a0c8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::CreateObjectNoConstructor
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

沒有建構函式以建立物件。  
  
## 語法  
  
```cpp#  
HRESULT CreateObjectNoConstructor(   
   IDebugField*   pClassObject,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateObjectNoConstructor(  
   IDebugField      pClassField,   
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `pClassObject`  
 \[in\][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，表示要建立物件的型別。  
  
 `ppObject`  
 \[\] out傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表剛建立的物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法來建立物件，表示執行個體的結構或複雜型別 \(也就不需要建構函式\) 是函式的參數，這由[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  
  
 如果物件參數需要一個建構函式，呼叫[建立物件](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)方法。  
  
## 請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [建立物件](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)