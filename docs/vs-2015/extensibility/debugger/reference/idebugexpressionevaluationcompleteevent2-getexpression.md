---
title: IDebugExpressionEvaluationCompleteEvent2::GetExpression |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51d993e34d5be3b8d5c67ed2a601546242d9909b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816914"
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

取得原始的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
HRESULT GetExpression(   
   IDebugExpression2** ppExpr  
);  
```  
  
```csharp  
int GetExpression(   
   out IDebugExpression2 ppExpr  
);  
```  
  
#### <a name="parameters"></a>參數  
 `ppExpr`  
 [out]傳回[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)物件，表示已剖析的運算式。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會傳回呼叫中所建立的物件[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)

