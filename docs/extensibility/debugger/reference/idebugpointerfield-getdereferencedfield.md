---
title: "IDebugPointerField::GetDereferencedField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPointerField::GetDereferencedField"
helpviewer_keywords: 
  - "IDebugPointerField::GetDereferencedField 方法"
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會傳回這個指標物件所指向的物件型別。  
  
## 語法  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```c#  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### 參數  
 `ppField`  
 \[\] out傳回[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)描述型別的目標物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 例如，如果[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)物件是指為一個整數， [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)這個方法傳回型別告訴您，該整數型別。  
  
## 請參閱  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)