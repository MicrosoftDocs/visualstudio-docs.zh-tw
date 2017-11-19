---
title: "IDebugExpressionEvaluator2::PreloadModules |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaceac744b06a44e3ef73de6cc9eda7255e59cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
預先載入指定的符號提供者所指定的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT PreloadModules (  
   IDebugSymbolProvider* pSym  
);  
```  
  
```csharp  
int PreloadModules (  
   IDebugSymbolProvider pSym  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSym`  
 [in]其會預先載入模組的符號提供者。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 您執行裝載處理序附加時，會使用這個選擇性的方法。 它可讓 EE '準備' 做為附加的一部分。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來**ExpressionEvaluatorPackage**公開物件[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)介面。  
  
```cpp  
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)