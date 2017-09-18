---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

呼叫事件處理常式來擷取相關符號的載入程序的結果。  
  
## 語法  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### 參數  
 `pModule`  
 \[\] outIDebugModule3 物件，表示已載入符號的模組。  
  
 `pbstrDebugMessage`  
 輸入 \[、 輸出\]傳回字串，包含從模組的任何錯誤訊息。  如果沒有任何錯誤訊息，然後這個字串只會包含模組的名稱，但不會是空。  
  
> [!NOTE]
>  \[C\+\+\]`pbstrDebugMessage`不能`NULL` ，必須釋放與`SysFreeString`。  
  
 `pdwModuleInfoFlags`  
 \[\] out從的旗標組合[MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)列舉型別，指出是否已載入任何符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  
  
## 備註  
 當處理常式會收到[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)事件之後嘗試載入模組的偵錯符號，這個處理常式可以呼叫 thismethod，以判斷該負載的結果。  
  
## 請參閱  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)