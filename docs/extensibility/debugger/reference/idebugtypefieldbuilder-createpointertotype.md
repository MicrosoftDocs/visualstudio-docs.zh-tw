---
title: "IDebugTypeFieldBuilder::CreatePointerToType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePointerToType"
  - "IDebugTypeFieldBuilder::CreatePointerToType"
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

建立指定型別的指標。  
  
## 語法  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```c#  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### 參數  
 `pTypeField`  
 \[in\]要移向 \[型別。  它由[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。  
  
 `pPtrToTypeField`  
 \[\] out傳回代表新指標 **IDebugField** 物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)