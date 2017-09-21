---
title: "IDebugExpressionEvaluator2::PreloadModules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::PreloadModules"
  - "PreloadModules"
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugExpressionEvaluator2::PreloadModules
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

預先載入指定的符號提供者所指定的模組。  
  
## 語法  
  
```cpp#  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```c#  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### 參數  
 `pSym`  
 \[in\]其會預先載入的模組的符號提供者。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 當您執行這項裝載處理序附加，則會使用這個選擇性的方法。  它提供得知 ee 給予 '準備' 附加的一部分的機率。  
  
## 範例  
 下列範例會示範如何實作這個方法，如 **ExpressionEvaluatorPackage** 物件，公開 \(expose\) [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)介面。  
  
```cpp#  
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules  
(  
    IDebugSymbolProvider *pSym  
)  
{  
    HRESULT hr = NOERROR;  
    RuntimeMemberDescriptor  * prtMemberDesc;  
    RuntimeClassDescriptor *prtClassDesc;  
    CComPtr<IDebugClassField> pClassField;  
    IfFalseGo(pSym,E_INVALIDARG);  
  
    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
    pClassField = NULL;  
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);  
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);  
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);  
  
Error:  
    return hr;  
}  
```  
  
## 請參閱  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)