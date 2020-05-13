---
title: IDebug運算式評估完成事件2::獲取運算式 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c6ed79edadf9191604291a4c6f0f07b0aa1f0dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729584"
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
獲取原始表達式。

## <a name="syntax"></a>語法

```cpp
HRESULT GetExpression( 
   IDebugExpression2** ppExpr
);
```

```csharp
int GetExpression( 
   out IDebugExpression2 ppExpr
);
```

## <a name="parameters"></a>參數
`ppExpr`\
[出]返回表示已解析的表達式的[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)物件。

## <a name="return-value"></a>傳回值
 如果成功,返回`S_OK`;否則,返回錯誤代碼。

## <a name="remarks"></a>備註
 此方法返回在調用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法時創建的物件。

## <a name="see-also"></a>另請參閱
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
