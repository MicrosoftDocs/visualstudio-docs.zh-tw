---
title: "IDebugField::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetAddress"
helpviewer_keywords: 
  - "IDebugField::GetAddress 方法"
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得偵錯欄位的位址。  
  
## 語法  
  
```cpp#  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### 參數  
 `ppAddress`  
 \[\] out傳回與位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，傳回錯誤碼。  
  
## 請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)