---
description: 這個方法會以非同步方式評估運算式。
title: IDebugExpression2：： EvaluateAsync |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bea7a5a05dc5277e693d033452f0b4e7342ea946
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092419"
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

## <a name="parameters"></a>參數
`dwFlags`\
在 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 列舉中的旗標組合，可控制運算式評估。

`pExprCallback`\
在此參數一律為 null 值。

## <a name="return-value"></a>傳回值
如果成功，則傳回，否則會傳回 `S_OK` 錯誤碼。 一般錯誤碼為：

|錯誤|描述|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|目前正在評估另一個運算式，但不支援同時運算式評估。|

## <a name="remarks"></a>備註
這個方法應該會在開始進行運算式評估之後立即傳回。 成功評估運算式後，必須透過[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，將[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)傳送至[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)事件回呼。

## <a name="example"></a>範例
下列範例示範如何針對實 IDebugExpression2 介面的簡單物件，執行這個方法 `CExpression` 。 [](../../../extensibility/debugger/reference/idebugexpression2.md)

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
