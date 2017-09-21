---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個文件內容來源的程式碼範圍。  
  
## 語法  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### 參數  
 `pBegPosition`  
 輸入 \[、 輸出\]A [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)會被填入的開始位置的結構。  如果不需要這項資訊，請設定此引數設為 null 值。  
  
 `pEndPosition`  
 輸入 \[、 輸出\]A [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)會被填入的結束位置的結構。  如果不需要這項資訊，請設定此引數設為 null 值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 來源範圍是程式碼中，從目前的陳述式後面，只要在前面產生的程式碼的陳述式之後的整個範圍。  來源範圍通常用於混合來源陳述式，包括註解，以在 \[反組譯碼\] 視窗中的程式碼。  
  
 若要取得範圍只包含在本文中的文件中的程式碼陳述，呼叫[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)方法。  
  
## 請參閱  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)