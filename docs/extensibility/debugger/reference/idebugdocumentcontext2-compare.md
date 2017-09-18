---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

比較這個文件內容，以指定之陣列的文件內容。  
  
## 語法  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### 參數  
 `compare`  
 \[in\]介於[DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)指定的比較類型的列舉型別。  
  
 `rgpDocContextSet`  
 \[in\]陣列的[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)代表所要比較的文件內容的物件。  
  
 `dwDocContextSetLen`  
 \[in\]若要比較的文件內容的陣列的長度。  
  
 `pdwDocContext`  
 \[\] out傳回指數`rgpDocContextSet`滿足比較的第一個文件內容的陣列。  
  
## 傳回值  
 傳回`S_OK`如果找不到相符的項目。  傳回`S_FALSE`如果找不到任何符合的項目。  否則，會傳回錯誤碼。  
  
## 備註  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)在陣列中傳遞的物件必須實作相同的偵錯引擎實作`IDebugDocumentContext2`上 ； 呼叫的物件 否則，比較不正確。  
  
## 請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)