---
description: 這個介面會將符號欄位（通常由符號提供者傳回）系結至記憶體內容或包含符號目前值的物件。
title: IDebugBinder |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4fdfe0cffce209880d870cde7b70cc1e02252413
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089078"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面會將符號欄位（通常由符號提供者傳回）系結至記憶體內容或包含符號目前值的物件。

## <a name="syntax"></a>Syntax

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面支援運算式評估，並且必須由 debug engine (DE) 來執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 此介面會在運算式評估的過程中使用，且通常用於 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 和 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)的實。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugBinder` 。

|方法|描述|
|------------|-----------------|
|[綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)|取得包含符號目前值的記憶體內容或物件。|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|判斷物件的執行時間類型。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|將物件位置或記憶體位址轉換成記憶體內容。|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|取得用來建立函數參數的 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 物件。|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|取得變數的確切型別。|

## <a name="remarks"></a>備註
 此介面會傳回剖析樹狀結構中運算式評估工具所使用的物件。 運算式評估工具會使用符號提供者來剖析運算式，將運算式中的符號轉換成 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)的實例，這會根據原始程式碼中的型別和位置來描述每個符號。 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法會將 `IDebugField` 物件轉換成[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件，以便將符號類型連接或系結至記憶體中的實際值。 這些 `IDebugObject` 物件接著會儲存在剖析樹狀結構中，以供稍後評估之用。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
