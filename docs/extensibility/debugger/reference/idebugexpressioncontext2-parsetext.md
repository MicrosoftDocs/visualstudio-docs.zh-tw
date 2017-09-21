---
title: "IDebugExpressionContext2::ParseText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionContext2::ParseText"
helpviewer_keywords: 
  - "IDebugExpressionContext2::ParseText"
ms.assetid: f58575db-f926-4ac8-83ff-7b3b86ab61e2
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionContext2::ParseText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

剖析文字形式進行後續的評估運算式。  
  
## 語法  
  
```cpp#  
HRESULT ParseText(   
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2** ppExpr,  
   BSTR*               pbstrError,  
   UINT*               pichError  
);  
```  
  
```c#  
int ParseText(   
   string                pszCode,  
   enum_PARSEFLAGS       dwFlags,  
   uint                  nRadix,  
   out IDebugExpression2 ppExpr,  
   out string            pbstrError,  
   out uint              pichError  
);  
```  
  
#### 參數  
 `pszCode`  
 \[in\]要剖析的運算式。  
  
 `dwFlags`  
 \[in\]從的旗標組合[PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)控制剖析的列舉型別。  
  
 `nRadix`  
 \[in\]若要使用於剖析中的任何數字資訊的基數`pszCode`。  
  
 `ppExpr`  
 \[\] out傳回[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)物件，代表已剖析的運算式中，已準備好進行繫結和評估。  
  
 `pbstrError`  
 \[\] out如果運算式包含錯誤，則傳回的錯誤訊息。  
  
 `pichError`  
 \[\] out傳回字元的索引中的錯誤訊息`pszCode`如果運算式包含錯誤。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當呼叫這個方法時，偵錯引擎 \(DE\) 應該剖析運算式，並驗證它正確。  `pbstrError`和`pichError`可能會在填寫參數，如果運算式是不正確。  
  
 請注意無法評估運算式，只剖析。  稍後呼叫[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法會計算已剖析的運算式。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CEnvBlock`物件，公開 \(expose\) [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  本範例會考慮要剖析為環境變數名稱的運算式，並擷取來自該變數的值。  
  
```cpp#  
HRESULT CEnvBlock::ParseText(  
   LPCOLESTR           pszCode,  
   PARSEFLAGS          dwFlags,  
   UINT                nRadix,  
   IDebugExpression2 **ppExpr,  
   BSTR               *pbstrError,  
   UINT               *pichError)  
{  
   HRESULT hr = E_OUTOFMEMORY;    
   // Create an integer variable with a value equal to one plus    
   // twice the length of the passed expression to be parsed.    
   int iAnsiLen      = 2 * (wcslen(pszCode)) + 1;    
   // Allocate a character string of the same length.    
   char *pszAnsiCode = (char *) malloc(iAnsiLen);    
  
   // Check for successful memory allocation.    
   if (pszAnsiCode) {    
      // Map the wide-character pszCode string to the new pszAnsiCode character string.    
      WideCharToMultiByte(CP_ACP, 0, pszCode, -1, pszAnsiCode, iAnsiLen, NULL, NULL);    
      // Check to see if the app can succesfully get the environment variable.    
      if (GetEnv(pszAnsiCode)) {    
  
         // Create and initialize a CExpression object.    
         CComObject<CExpression> *pExpr;    
         CComObject<CExpression>::CreateInstance(&pExpr);    
            pExpr->Init(pszAnsiCode, this, NULL);    
  
         // Assign the pointer to the new object to the passed argument  
         // and AddRef the object.    
         *ppExpr = pExpr;    
         (*ppExpr)->AddRef();    
         hr = S_OK;    
      // If the program cannot succesfully get the environment variable.    
      } else {    
         // Set the errror message and return E_FAIL.    
         *pbstrError = SysAllocString(L"No such environment variable.");    
         hr = E_FAIL;    
      }    
      // Free the local character string.    
      free(pszAnsiCode);    
   }    
   return hr;    
}    
```  
  
## 請參閱  
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)