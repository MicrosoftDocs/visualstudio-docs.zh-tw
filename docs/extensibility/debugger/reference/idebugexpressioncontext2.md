---
title: IDebug運算式上下文2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729635"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
此介面表示運算式運算的上下文

## <a name="syntax"></a>語法

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示可以計算運算式上下文。

## <a name="notes-for-callers"></a>通話備註
 對[GetExpressionContext 的](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)呼叫將返回此介面。 僅當正在調試的程式已暫停且堆疊幀可用時,才能訪問此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugExpressionContext2`。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|檢索評估上下文的名稱。|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|分析用於計算的基於文本的運算式。|

## <a name="remarks"></a>備註
 可以將評估上下文視為執行表達式計算的範圍。

 當程式停止時,工作階段除錯管理員 (SDM) 從 DE 取得一個堆疊幀,並呼叫[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後,SDM 調用[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)`IDebugExpressionContext2`來獲取介面。 然後調用[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)以建立[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)介面,該介面表示可供計算的解析運算式。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
