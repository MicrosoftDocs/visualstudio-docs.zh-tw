---
title: "IDebugReference2::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::GetParent"
helpviewer_keywords: 
  - "IDebugReference2::GetParent"
ms.assetid: e3061665-ad3e-4c1b-b33f-82755fa21be3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得父參考的參考。  保留供將來使用。  
  
## 語法  
  
```cpp#  
HRESULT GetParent (   
   IDebugReference2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugReference2 ppParent  
);  
```  
  
#### 參數  
 `ppParent`  
 \[\] out傳回[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) ，表示這個屬性的父代的物件。  
  
## 傳回值  
 永遠傳回 `E_NOTIMPL`。  
  
## 請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)