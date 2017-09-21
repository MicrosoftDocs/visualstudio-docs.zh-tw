---
title: "IDebugCanStopEvent2::GetDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugCanStopEvent2::GetDocumentContext"
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCanStopEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得描述這個事件的位置的文件內容。  
  
## 語法  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### 參數  
 `ppDocCxt`  
 \[\] out傳回[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)介面，代表目前的程式碼所在位置的對應來源檔案文件中的位置。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 一般而言，文件內容可以被視為原始程式檔中的位置。  
  
 若要取得程式碼內容，也就是向 \[程式碼指示的方向，呼叫[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)方法。  
  
## 請參閱  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)