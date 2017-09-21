---
title: "IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

判斷指定的文件中若包含文件位置。  
  
## 語法  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```c#  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### 參數  
 `pDoc`  
 \[in\][IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)物件，代表包含的文件候選。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法主要用於將中斷點設定[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面。  當載入文件時，中斷點位置稱為以判斷文件是否包含這個位置。  
  
## 請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)