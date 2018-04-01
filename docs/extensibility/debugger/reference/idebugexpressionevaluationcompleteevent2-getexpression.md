---
title: IDebugExpressionEvaluationCompleteEvent2::GetExpression |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 96157885fa37edc9216086359a898e5191ce2444
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
取得原始的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。  
  
## <a name="remarks"></a>備註  
 這個方法會傳回物件的呼叫中所建立[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法。  
  
## <a name="see-also"></a>請參閱  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)