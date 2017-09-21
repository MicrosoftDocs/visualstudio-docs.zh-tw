---
title: "IDebugMethodField::GetGlobalContainer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetGlobalContainer"
helpviewer_keywords: 
  - "IDebugMethodField::GetGlobalContainer 方法"
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetGlobalContainer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得通用容器的方法。  
  
## 語法  
  
```cpp#  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### 參數  
 `ppClass`  
 \[\] out傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)代表用來定義這個方法的模組。  
  
## 傳回值  
 如果成功的話，則傳回 S\_OK。 否則，會傳回錯誤碼。  
  
## 備註  
 傳回[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)物件代表整個模組，而是人為物件，也就是模組本身並沒有實際的類別但它只能透過`IDebugClassField`物件，讓要列舉並發現模組的各種元素。  
  
## 請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)