---
title: "IDebugDocumentPosition2::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetFileName"
ms.assetid: d713635e-088f-465b-b26d-00ac971c9e86
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetFileName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得包含文件位置的原始程式檔的檔名。  
  
## 語法  
  
```cpp#  
HRESULT GetFileName(   
   BSTR* pbstrFileName  
);  
```  
  
```c#  
int GetFileName(   
   out string pbstrFileName  
);  
```  
  
#### 參數  
 `pbstrFileName`  
 \[\] out傳回原始程式檔的檔名。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 原始程式檔可能不一定都會有檔名 \(原始程式檔可能不存在磁碟，例如\)。  
  
## 請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)