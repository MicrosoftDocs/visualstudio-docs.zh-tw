---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 03ece802cc05e269dac26794bbc19e7a06b0679d
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
This method evaluates the expression asynchronously.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parameters  
 `dwFlags`  
 [in] A combination of flags from the [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeration that control expression evaluation.  
  
 `pExprCallback`  
 [in] This parameter is always a null value.  
  
## <a name="return-value"></a>Return Value  
 If successful, returns `S_OK`; otherwise returns an error code. A typical error code is:  
  
|Error|Description|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Another expression is currently being evaluated, and simultaneous expression evaluation is not supported.|  
  
## <a name="remarks"></a>Remarks  
 This method should return immediately after it has started the expression evaluation. When the expression is successfully evaluated, an [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) must be sent to the [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) event callback as supplied through [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) or [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Example  
 The following example shows how to implement this method for a simple `CExpression` object that implements the [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interface.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>See Also  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
