---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e084152f6215878816739f46dc91fa322cf9c94
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945155"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個方法會以非同步方式評估的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
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
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)控制運算式評估的列舉型別。  
  
 `pExprCallback`  
 [in]此參數一律為 null 值。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則傳回`S_OK`; 否則會傳回錯誤碼。 典型的錯誤碼是：  
  
|錯誤|描述|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在評估另一個運算式，並不支援同時的運算式評估。|  
  
## <a name="remarks"></a>備註  
 此方法應在開始運算式評估之後，立即傳回。 成功評估運算式時， [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)必須傳送至[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)透過提供的事件回呼[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或是[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CExpression`實作的物件[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
```cpp#  
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
