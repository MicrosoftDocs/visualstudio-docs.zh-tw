---
title: "IDebugExpressionEvaluator::GetMethodProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodProperty 方法"
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會取得屬性的物件，包含區域變數、 引數及其他屬性的方法。  
  
## 語法  
  
```cpp#  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### 參數  
 `pSymbolProvider`  
 \[in\]符號提供者，以供使用，表示成[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件。  
  
 `pAddress`  
 \[in\]在 \[程式碼，以表示位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件，應該解析為最接近的包含函式。  
  
 `pBinder`  
 \[in\]繫結器使用，表示成[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。  
  
 `fIncludeHiddenLocals`  
 \[in\]非零值 \(`TRUE`\) 表示要包含隱藏的區域變數。 零 \(`FALSE`\) 表示要排除隱藏的區域變數  
  
 `ppProperty`  
 \[\] out傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，其表示方法的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 隱藏的區域變數通常是由編譯器所產生的變數。  
  
## 請參閱  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)