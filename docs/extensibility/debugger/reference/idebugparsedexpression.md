---
title: IDebugsered 運算式 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugParsedExpression
helpviewer_keywords:
- IDebugParsedExpression interface
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22069b8eedb06d67eafaf7333f379a057c1b6f23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726004"
---
# <a name="idebugparsedexpression"></a>IDebugParsedExpression
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示可供計算的已解析表達式。

## <a name="syntax"></a>語法

```
IDebugParsedExpression : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式評估器實現此介面以表示可供計算的解析表達式。

## <a name="notes-for-callers"></a>通話備註
 對[Parse 的](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)調用將返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugParsedExpression`。

|方法|描述|
|------------|-----------------|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|計算解析的運算式。|

## <a name="remarks"></a>備註
 當調用方準備計算表達式時,它將調用[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)返回包含計算結果的[IDebugProperty2。](../../../extensibility/debugger/reference/idebugproperty2.md) 這種由兩部分組成的計算方法(分析然後計算)使解析的表達式能夠多次計算,從而繞過分析表達式的耗時過程。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
