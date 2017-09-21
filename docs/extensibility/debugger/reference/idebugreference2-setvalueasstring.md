---
title: "IDebugReference2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsString"
ms.assetid: 9a508ced-fd54-44f5-bb42-ec15c80384d7
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

設定值，從字串的參考。  保留供將來使用。  
  
## 語法  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   dwRadix,  
   uint   dwTimeout  
);  
```  
  
#### 參數  
 `pszValue`  
 \[in\]做為字串值。  
  
 `dwRadix`  
 \[in\]要用於格式化數字的任何資訊基數。  
  
 `dwTimeout`  
 \[in\]最大時間 \(毫秒\)，從這個方法傳回之前等待。  使用`INFINITE`無限期地等待。  
  
## 傳回值  
 永遠傳回 `E_NOTIMPL`。  
  
## 請參閱  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)