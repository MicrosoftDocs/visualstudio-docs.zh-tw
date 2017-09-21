---
title: "IDebugParsedExpression::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugParsedExpression::EvaluateSync"
helpviewer_keywords: 
  - "IDebugParsedExpression::EvaluateSync 方法"
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugParsedExpression::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會剖析的運算式的評估，並選擇性地轉換到另一種資料類型的結果。  
  
## 語法  
  
```cpp#  
HRESULT EvaluateSync(   
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BSTR                  bstrResultType,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   uint                 dwEvalFlags,   
   uint                 dwTimeout,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   string               bstrResultType,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### 參數  
 `dwEvalFlags`  
 \[in\]結合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)的常數，控制要評估的運算式的方式。  
  
 `dwTimeout`  
 \[in\]以毫秒為單位，這個方法傳回之前等待指定的最長的時間。  使用`INFINITE`無限期地等待。  
  
 `pSymbolProvider`  
 \[in\]符號提供者，以表示[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面。  
  
 `pAddress`  
 \[in\]在方法中，以表示目前的執行位置[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
 `pBinder`  
 \[in\]繫結器，以表示[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面。  
  
 `bstrResultType`  
 \[in\]結果的型別必須可以轉換成。  此引數可以是 null 值。  
  
 `ppResult`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面，表示評估的結果。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 運算式評估內容由提供 `pAddress`，因而可以判斷包含的方法，然後使用語言範圍規則來決定在運算式中的符號值。  
  
## 請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)