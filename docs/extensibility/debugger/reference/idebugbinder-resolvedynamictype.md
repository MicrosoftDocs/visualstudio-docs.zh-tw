---
title: "IDebugBinder::ResolveDynamicType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::ResolveDynamicType"
helpviewer_keywords: 
  - "IDebugBinder::ResolveDynamicType 方法"
ms.assetid: 2c36ef92-5b44-4cfd-988e-54a2e5a6710c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugBinder::ResolveDynamicType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回一個變數的精確型別。  
  
## 語法  
  
```cpp#  
HRESULT ResolveDynamicType (  
   IDebugDynamicField *pDynamic,  
   IDebugField       **ppResolved  
);  
```  
  
```c#  
int ResolveDynamicType(  
   IDebugDynamicField pDynamic,   
   out IDebugField    ppResolved  
);  
```  
  
#### 參數  
 `pDynamic`  
 \[in\][IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)代表變數的型別。  
  
 `ppResolved`  
 \[\] out傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)提供變數的型別相關的特定資訊。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)