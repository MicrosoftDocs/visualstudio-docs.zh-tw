---
title: "IDebugDocument2::GetDocumentClassID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
helpviewer_keywords: 
  - "IDebugDocument2::GetDocumentClassID"
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocument2::GetDocumentClassID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得文件的類別識別項。  
  
## 語法  
  
```cpp#  
HRESULT GetDocumentClassID(   
   CLSID* pclsid  
);  
```  
  
```c#  
int GetDocumentClassID(   
   out Guid pclsid  
);  
```  
  
#### 參數  
 `pclsid`  
 \[\] out傳回文件的類別 id 的 GUID。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 類別 GUID 可用來具現化每一個都代表文件的個別類別。  
  
## 請參閱  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)