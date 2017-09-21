---
title: "IDebugProgram2::EnumCodeContexts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodeContexts"
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

擷取一份原始程式檔中的指定位置的程式碼內容。  
  
## 語法  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```c#  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### 參數  
 `pDocPos`  
 \[in\][IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)物件，表示已知 IDE 的原始程式檔中的抽象座標。  
  
 `ppEnum`  
 \[\] out傳回[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)物件，其中包含的程式碼內容的清單。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法可讓工作階段偵錯管理員 」 \(SDM\) 或適用於 IDE 來對應到的程式碼指定位置的來源檔案位置。  如果來源所產生的程式碼 \(例如，c \+ \+ 樣板\) 的多個區塊，則傳回一個以上的程式碼內容。  
  
## 請參閱  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)