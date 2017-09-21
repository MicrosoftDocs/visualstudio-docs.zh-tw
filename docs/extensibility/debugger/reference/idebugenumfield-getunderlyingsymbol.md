---
title: "IDebugEnumField::GetUnderlyingSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetUnderlyingSymbol"
helpviewer_keywords: 
  - "IDebugEnumField::GetUnderlyingSymbol 方法"
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetUnderlyingSymbol
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) ，表示此列舉型別的名稱。  
  
## 語法  
  
```cpp#  
HRESULT GetUnderlyingSymbol(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetUnderlyingSymbol(  
   out IDebugField ppField  
);  
```  
  
#### 參數  
 `ppField`  
 \[\] out傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述這個列舉型別的名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 列舉型別的名稱雷同的列舉型別，會使用繫結至的記憶體位置的型別[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)。  
  
## 請參閱  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)