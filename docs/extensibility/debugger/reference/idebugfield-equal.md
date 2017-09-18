---
title: "IDebugField::Equal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::Equal"
helpviewer_keywords: 
  - "IDebugField::Equal 方法"
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::Equal
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會比較此欄位與指定的欄位相等。  
  
## 語法  
  
```cpp#  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```c#  
int Equal(  
   IDebugField pField  
);  
```  
  
#### 參數  
 `pField`  
 \[in\]比較這個欄位。  
  
## 傳回值  
 如果欄位是相同時，會傳回`S_OK`。  如果欄位不同，會傳回`S_FALSE.`否則會傳回錯誤碼。  
  
## 請參閱  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)