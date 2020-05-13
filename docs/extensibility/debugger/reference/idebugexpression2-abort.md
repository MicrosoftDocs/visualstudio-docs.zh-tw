---
title: IDebugExpression2::中止 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729769"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
此方法取消由對[評估 Async](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法調用啟動的非同步表達式計算。

## <a name="syntax"></a>語法

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 取消非同步表示式計算後,不要向傳遞給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)或[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)方法的事件回檔發送[IDebugExpressionExpressionExpressionExpressionCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)事件。

## <a name="see-also"></a>另請參閱
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
