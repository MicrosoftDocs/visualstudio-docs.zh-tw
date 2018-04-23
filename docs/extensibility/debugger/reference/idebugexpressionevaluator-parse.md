---
title: IDebugExpressionEvaluator::Parse |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a10a65564682b5c82350eb5c22af3f217a3a993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
這個方法會將運算式字串轉換成剖析的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>參數  
 `upstrExpression`  
 [in]要剖析的運算式字串。  
  
 `dwFlags`  
 [in]集合[PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)常數，決定要如何剖析運算式。  
  
 `nRadix`  
 [in]用來解譯任何數字資訊的基數。  
  
 `pbstrError`  
 [out]以人類看得懂的文字會傳回錯誤。  
  
 `pichError`  
 [out]傳回字元位置開始的錯誤中的運算式字串。  
  
 `ppParsedExpression`  
 [out]傳回剖析的運算式中[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)物件。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會產生已剖析的運算式，而不實際的值。 剖析的運算式已準備好進行評估，也就是轉換成的值。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)