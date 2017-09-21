---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得這個文件位置的範圍。  
  
## 語法  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
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
 位置中斷點的文件位置中指定的範圍，偵錯引擎 \(DE\) 用以搜尋繼續進行的陳述式中實際提供的程式碼。  例如，請參考下列程式碼：  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 第 5 行提供任何的程式碼，以進行偵錯的程式。  如果偵錯工具會在第 5 行上設定中斷點，想要向前搜尋特定量可提供程式碼第一行 DE，偵錯工具會指定一個範圍包含額外的候選位置可能適當地放置中斷點的行。  DE 會再向前搜尋這些行直到它找到無法接受中斷點一條線。  
  
## 請參閱  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)