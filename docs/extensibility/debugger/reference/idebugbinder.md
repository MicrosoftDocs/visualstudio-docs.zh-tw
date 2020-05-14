---
title: IDebugBinder |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcdec19c4667356edaf9e057c86ddc24baf747b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735967"
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面將符號欄位(通常由符號提供程式返回)綁定到包含符號當前值的記憶體上下文或物件。

## <a name="syntax"></a>語法

```
IDebugBinder : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面支援表達式計算,必須由調試引擎 (DE) 實現。

## <a name="notes-for-callers"></a>通話備註
 此介面用於表示式計算過程,通常用於[評估同步](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[評估Async](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBinder`。

|方法|描述|
|------------|-----------------|
|[綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)|獲取包含符號當前值的記憶體上下文或物件。|
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|確定物件的運行時類型。|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|將物件位置或記憶體位址轉換為記憶體上下文。|
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|取得用於建立函數參數的[IDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)。|
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|獲取變數的確切類型。|

## <a name="remarks"></a>備註
 此介面返回表達式賦值器在解析樹中使用的物件。 表達式賦值器通過使用符號提供程式將運算式中的符號轉換為[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)的實例來解析表達式,IDebugField 根據其類型和在原始碼中的位置來描述每個符號。 [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法`IDebugField`將 物件轉換為[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md),這些物件將符號類型連接或綁定到記憶體中的實際值。 然後`IDebugObject`,這些物件存儲在解析樹中,以供以後評估。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
