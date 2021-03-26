---
title: IDebugExpressionCoNtext2 |Microsoft Docs
description: 此介面代表運算式評估的內容
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6d8745207f1ab075aedd43815e7a97a4f0721bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092289"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
此介面代表運算式評估的內容。

## <a name="syntax"></a>Syntax

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表可評估運算式的內容。

## <a name="notes-for-callers"></a>呼叫者注意事項
 對 [GetExpressionCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 的呼叫會傳回這個介面。 只有在正在進行程式設計的程式已暫停，而且有堆疊框架可用時，才可以存取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugExpressionContext2` 。

|方法|描述|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|抓取評估內容的名稱。|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|剖析以文字為基礎的運算式以進行評估。|

## <a name="remarks"></a>備註
 評估內容可以視為執行運算式評估的範圍。

 當程式停止時，會話 debug manager (SDM) 從 EnumFrameInfo 取得堆疊框架，並呼叫[](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後 SDM 會呼叫 [GetExpressionCoNtext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) 以取得 `IDebugExpressionContext2` 介面。 接下來就是呼叫 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 來建立 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 介面，此介面表示準備要評估的已剖析運算式。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
