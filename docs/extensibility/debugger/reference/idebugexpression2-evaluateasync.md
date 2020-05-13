---
title: IDebugExpression2::評估同步 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729759"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
此方法非同步計算表達式。

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

## <a name="parameters"></a>參數
`dwFlags`\
[在][EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉中的標誌的組合,用於控制運算式計算。

`pExprCallback`\
[在]此參數始終為空值。

## <a name="return-value"></a>傳回值
如果成功,返回`S_OK`;否則返回錯誤代碼。 典型的錯誤代碼是:

|錯誤|描述|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在計算另一個表達式,並且不支援同時計算表達式。|

## <a name="remarks"></a>備註
此方法應在開始表達式計算后立即返回。 成功計算運算式後,必須將[IDebugExpressionExpression 評估完成事件2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)發送到[IDebugEvent 回檔2](../../../extensibility/debugger/reference/idebugeventcallback2.md)事件回調,透過[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)提供。

## <a name="example"></a>範例
下面的範例展示如何實現[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面的簡單`CExpression`物件實現此方法。

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
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
