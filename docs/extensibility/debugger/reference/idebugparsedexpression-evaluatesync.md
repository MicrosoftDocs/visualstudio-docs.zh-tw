---
title: IDebugParsedExpression::EvaluateSync |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugParsedExpression::EvaluateSync
helpviewer_keywords:
- IDebugParsedExpression::EvaluateSync method
ms.assetid: 0ea04cfa-de87-4b6c-897e-4572c1a28942
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b67294b6bb22ff9607be726415b6aae8a2a9524
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugparsedexpressionevaluatesync"></a>IDebugParsedExpression::EvaluateSync
這個方法會剖析的運算式評估，並選擇性地將轉換為其他資料類型的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
```csharp  
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
  
#### <a name="parameters"></a>參數  
 `dwEvalFlags`  
 [in]組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)控制要如何評估運算式的常數。  
  
 `dwTimeout`  
 [in]指定的時間上限，以毫秒為單位，從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `pSymbolProvider`  
 [in]符號提供者，以表示[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)介面。  
  
 `pAddress`  
 [in]目前的執行位置在方法中，以表示[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面。  
  
 `pBinder`  
 [in]繫結器，以表示[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面。  
  
 `bstrResultType`  
 [in]結果的類型應該轉換成。 這個引數可以是 null 值。  
  
 `ppResult`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面代表評估的結果。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 運算式評估內容由提供`pAddress`這可讓它來判斷包含方法，然後使用語言範圍規則可決定在運算式中的符號的值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)