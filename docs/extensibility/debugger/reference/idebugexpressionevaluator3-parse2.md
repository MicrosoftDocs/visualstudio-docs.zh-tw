---
title: "IDebugExpressionEvaluator3::Parse2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator3::Parse2"
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator3::Parse2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

要剖析的運算式，根據指定的符號提供者和鑑定的畫面格的位址，將轉換的運算式字串。  
  
## 語法  
  
```cpp#  
HRESULT Parse2 (  
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   IDebugSymbolProvider*    pSymbolProvider,  
   IDebugAddress*           pAddress,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```c#  
HRESULT Parse2 (  
   string                     upstrExpression,  
   enum_PARSEFLAGS            dwFlags,  
   uint                       nRadix,  
   IDebugSymbolProvider       pSymbolProvider,  
   IDebugAddress              pAddress,  
   out string                 pbstrError,  
   out uint                   pichError,  
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### 參數  
 `upstrExpression`  
 \[in\]要剖析的運算式字串。  
  
 `dwFlags`  
 \[in\]一堆[PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)常數，以決定要剖析的運算式的方式。  
  
 `nRadix`  
 \[in\]要用來解譯數字的任何資訊的基數。  
  
 `pSymbolProvider`  
 \[in\]符號提供者的介面。  
  
 `pAddress`  
 \[in\]鑑定的框架位址。  
  
 `pbstrError`  
 \[\] out為人們可讀取的文字會傳回錯誤。  
  
 `pichError`  
 \[\] out運算式字串中傳回之錯誤開頭的字元位置。  
  
 `ppParsedExpression`  
 \[\] out傳回剖析的運算式，在[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 這個方法會產生剖析的運算式，不是實際的值。  剖析的運算式已準備好進行評估，也就是轉換為值。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **CEE** 物件，公開 \(expose\) [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)介面。  
  
```cpp#  
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,  
  PARSEFLAGS in_FLAGS,  
  UINT in_RADIX,  
  IDebugSymbolProvider *pSymbolProvider,  
  IDebugAddress *pAddress,  
  BSTR* out_pbstrError,  
  UINT* inout_pichError,  
  IDebugParsedExpression** out_ppParsedExpression )  
{  
    // precondition  
    REQUIRE( NULL != in_szExprText );  
    //REQUIRE( NULL != out_pbstrError );  
    REQUIRE( NULL != inout_pichError );  
    REQUIRE( NULL != out_ppParsedExpression );  
  
    if (NULL == in_szExprText)  
        return E_INVALIDARG;  
  
    if (NULL == inout_pichError)  
        return E_POINTER;  
  
    if (NULL == out_ppParsedExpression)  
        return E_POINTER;  
  
    if (out_pbstrError)  
        *out_pbstrError = NULL;  
  
    *out_ppParsedExpression = NULL;  
  
    INVARIANT( this );  
  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    // function body  
    EEDomain::fParseExpression DomainVal =  
    {  
        this,                   // CEE*  
        in_szExprText,          // LPCOLESTR  
        in_FLAGS,               // EVALFLAGS  
        in_RADIX,               // RADIX  
        out_pbstrError      ,   // BSTR*  
        inout_pichError,        // UINT*  
        pSymbolProvider,  
        out_ppParsedExpression  // Output  
    };  
  
    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);  
}  
```  
  
## 請參閱  
 [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)