---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters 方法"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立列舉值的方法的參數。  
  
## 語法  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### 參數  
 `ppParams`  
 \[\] out傳回[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)物件的參數清單的方法。 如果沒有參數，否則傳回 null 值。  
  
## 傳回值  
 如果成功的話，會傳回 S\_OK，或傳回 S\_FALSE，如果沒有參數。  否則，會傳回錯誤碼。  
  
## 備註  
 每個元素是[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，代表不同類型的參數。  呼叫[GetKind](../Topic/IDebugField::GetKind.md)方法來判斷到底什麼樣的參數物件所表示的每個物件上。  
  
 參數會包含其變數的名稱和其型別。  類別方法的第一個參數通常是"this"指標。  
  
 如果只需要參數型別時，呼叫[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)方法。  
  
## 請參閱  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)