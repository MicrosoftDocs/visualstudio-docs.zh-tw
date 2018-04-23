---
title: IDebugExpression2::EvaluateAsync |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13364d94f33eca33bf71b7077c19b9da54298ed7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
這個方法會以非同步方式評估運算式。  
  
## <a name="syntax"></a>語法  
  
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
  
#### <a name="parameters"></a>參數  
 `dwFlags`  
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)控制運算式評估的列舉。  
  
 `pExprCallback`  
 [in]這個參數一律是 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 典型的錯誤碼是：  
  
|錯誤|描述|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在評估另一個運算式，並不支援同時運算式評估。|  
  
## <a name="remarks"></a>備註  
 這個方法應該會啟動運算式評估之後，立即傳回。 當成功評估運算式時， [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)必須只能傳送到[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)做為透過提供的事件回呼[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CExpression`實作物件[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)