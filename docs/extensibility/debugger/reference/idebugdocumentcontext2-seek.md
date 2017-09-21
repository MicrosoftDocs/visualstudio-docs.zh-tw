---
title: "IDebugDocumentContext2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Seek"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Seek"
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

將文件內容移動指定的陳述式或程式行數。  
  
## 語法  
  
```cpp#  
HRESULT Seek(   
   int                      nCount,  
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```cpp#  
int Seek(   
   int                        nCount,  
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### 參數  
 `nCount`  
 \[in\]陳述式或將繼續進行，取決於文件內容的行數。  
  
 `ppDocContext`  
 \[\] out傳回新的[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)物件，做為新的位置。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)