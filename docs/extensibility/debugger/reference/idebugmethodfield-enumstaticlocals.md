---
title: "IDebugMethodField::EnumStaticLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumStaticLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumStaticLocals 方法"
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立方法的靜態區域變數的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### 參數  
 `ppLocals`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示靜態區域變數的清單。  如果不有任何靜態區域變數，則傳回 null 值。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或傳回 S\_FALSE，如果不有任何靜態區域變數。  否則，會傳回錯誤碼。  
  
## 備註  
 每個元素是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表不同的靜態區域變數的型別。  呼叫[GetKind](../Topic/IDebugField::GetKind.md)方法來判斷到底什麼樣的 static 區域變數物件所表示的每個物件上。  
  
## 請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)