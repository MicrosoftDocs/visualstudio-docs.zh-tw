---
title: "IDebugFunctionObject::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::Evaluate"
helpviewer_keywords: 
  - "IDebugFunctionObject::Evaluate 方法"
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

呼叫函式，並傳回產生的值做為物件。  
  
## 語法  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```c#  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### 參數  
 `ppParams`  
 \[in\]陣列的[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，並代表輸入的參數。  這些參數建立的其中一種`Create`中的方法[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。  
  
 `dwParams`  
 \[in\]中的參數數目`ppParams`陣列。  
  
 `dwTimeout`  
 \[in\]以毫秒為單位，這個方法傳回之前等待指定的最長的時間。  使用`INFINITE`無限期地等待。  
  
 `ppResult`  
 \[\] out傳回[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)表示做為物件的函式的值。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會設定並執行所表示的函式的呼叫[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)物件。  
  
## 請參閱  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)