---
title: "BP_LOCATION_CODE_STRING | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_STRING"
helpviewer_keywords: 
  - "BP_LOCATION_CODE_STRING 結構"
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

用來進行設定，使用者可以從整合式的開發環境 \(IDE\) 中輸入的字串為基礎的程式碼中斷點。  
  
## 語法  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## Members  
 `bstrContext`  
 程式碼內的中斷點，通常是方法或函式的名稱，做為 \[呼叫堆疊上看到的內容。  
  
 `bstrCodeExpr`  
 字串，使用者在型別來描述程式碼的中斷點。  
  
## 備註  
 這個結構屬於[BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)的聯集一部分的結構。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)