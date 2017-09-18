---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors 方法"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立這個類別的建構函式的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### 參數  
 `cMatch`  
 \[in\]介於[CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)指定的型別到列舉型別建構函式的列舉型別。  
  
 `ppEnum`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件，表示建構函式的清單。  如果沒有建構函式會傳回 null 值。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或者如果沒有建構函式會傳回 S\_FALSE。  否則，會傳回錯誤碼。  
  
## 備註  
 列舉型別的每個元素都是[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)物件，描述建構函式方法。  
  
 通常建構函式的清單不包括由編譯器所提供的預設建構函式。  
  
## 請參閱  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)