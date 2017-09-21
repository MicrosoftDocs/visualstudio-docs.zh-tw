---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject 方法"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立基本資料的物件，例如一個簡單的整數。  
  
## 語法  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### 參數  
 `ot`  
 \[in\]介於[OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md)列舉型別表示若要建立的原始物件的型別。  
  
 `ppObject`  
 \[\] out傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)代表剛建立的物件。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 呼叫這個方法來建立物件，表示它由函式參數的基本物件[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  比方說，如果運算式的字串為"myString\(5\)"，這個方法會用來建立物件，表示 5 的整數。  
  
## 請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)