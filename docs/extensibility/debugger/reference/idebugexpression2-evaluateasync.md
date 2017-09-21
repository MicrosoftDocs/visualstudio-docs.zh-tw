---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個方法會以非同步方式評估運算式。  
  
## 語法  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### 參數  
 `dwFlags`  
 \[in\]從的旗標組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)控制運算式評估的列舉型別。  
  
 `pExprCallback`  
 \[in\]這個參數永遠是 null 值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則會傳回錯誤碼。  典型的錯誤碼是:  
  
|錯誤|描述|  
|--------|--------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|目前在評估另一個運算式，並不支援同時的運算式評估。|  
  
## 備註  
 這個方法會在它啟動運算式評估之後，立即傳回。  成功地評估運算式時， [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)必須傳送至[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)事件的回呼，透過提供[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)。  
  
## 範例  
 下列範例會示範如何實作這個方法，如`CExpression`實作物件[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
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
  
## 請參閱  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)