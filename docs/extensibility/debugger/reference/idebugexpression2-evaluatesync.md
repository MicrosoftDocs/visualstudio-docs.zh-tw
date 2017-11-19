---
title: "IDebugExpression2::EvaluateSync |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2::EvaluateSync
helpviewer_keywords: IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ddc090e827b0a94a6534a0c4e625299cbc2ef5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
這個方法會以同步方式評估運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>參數  
 `dwFlags`  
 [in]從旗標的組合[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)控制運算式評估的列舉。  
  
 `dwTimeout`  
 [in]最大時間 （毫秒），從這個方法返回之前等候。 使用`INFINITE`無限期地等待。  
  
 `pExprCallback`  
 [in]這個參數一律是 null 值。  
  
 `ppResult`  
 [out]傳回[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件，其中包含的運算式評估結果。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回`S_OK`; 否則傳回錯誤碼。 一些典型的錯誤碼為：  
  
|錯誤|說明|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在評估另一個運算式，並不支援同時運算式評估。|  
|E_EVALUATE_TIMEOUT|評估已逾時。|  
  
## <a name="remarks"></a>備註  
 對於同步評估，則不需要回到 Visual Studio，評估完成時傳送事件。  
  
## <a name="example"></a>範例  
 下列範例示範如何實作這個方法來簡單`CExpression`實作物件[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
```cpp  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)