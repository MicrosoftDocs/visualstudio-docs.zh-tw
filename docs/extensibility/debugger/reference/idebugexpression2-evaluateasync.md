---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1585d68de7e2ea94961e72cf3f07fa9cd147f9b9
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56449810"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
這個方法會以非同步方式評估的運算式。

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
