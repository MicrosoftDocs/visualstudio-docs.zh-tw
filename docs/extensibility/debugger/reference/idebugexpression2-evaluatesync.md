---
title: IDebugExpression2::評估同步 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729683"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
此方法同步計算表達式。

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

## <a name="parameters"></a>參數
`dwFlags`\
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉中的標誌的組合,用於控制運算式計算。

`dwTimeout`\
[在]從此方法返回之前等待的最大時間(以毫秒為單位)。 用於`INFINITE`無限期等待。

`pExprCallback`\
[在]此參數始終為空值。

`ppResult`\
[出]返回包含表達式計算結果的[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則返回錯誤代碼。 一些典型的錯誤代碼是:

|錯誤|描述|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在計算另一個表達式,並且不支援同時計算表達式。|
|E_EVALUATE_TIMEOUT|評估超時。|

## <a name="remarks"></a>備註
對於同步評估,無需在評估完成後將事件發送回 Visual Studio。

## <a name="example"></a>範例
下面的範例展示如何實現[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面的簡單`CExpression`物件實現此方法。

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
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
