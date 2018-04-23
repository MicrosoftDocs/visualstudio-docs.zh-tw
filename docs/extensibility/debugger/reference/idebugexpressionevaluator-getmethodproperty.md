---
title: IDebugExpressionEvaluator::GetMethodProperty |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5d294e401af09ec3c10fa6dabbb878c661b559e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
這個方法會取得包含區域變數、 引數，以及方法的其他屬性的屬性物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSymbolProvider`  
 [in]要使用的符號提供者以[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)物件。  
  
 `pAddress`  
 [in]在程式碼，以表示位址[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件應該是解析成最接近包含函式。  
  
 `pBinder`  
 [in]要使用的繫結器表示為[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。  
  
 `fIncludeHiddenLocals`  
 [in]非零 (`TRUE`) 表示要包含隱藏 [區域變數]; 零 (`FALSE`) 表示要排除隱藏的區域變數  
  
 `ppProperty`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件表示的方法。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 隱藏 [區域變數] 通常是由編譯器產生的變數。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)