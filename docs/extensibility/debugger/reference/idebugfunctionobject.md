---
title: IDebugFunctionObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab1462c30f1012eb1002f692672fc470cac3b39a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921002"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示函式。

## <a name="syntax"></a>Syntax

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行這個介面來表示函式。

## <a name="notes-for-callers"></a>呼叫者注意事項
 此介面是 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面的特製化，而且是使用介面上的 [QueryInterface](/cpp/atl/queryinterface) 所取得 `IDebugObject` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)的方法之外，介面也會 `IDebugFunctionObject` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|建立基本資料物件。|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|使用函式建立物件。|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|建立沒有任何函式的物件。|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|建立陣列物件。|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|建立字串物件。|
|[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|呼叫函數，並傳回產生的值做為物件。|

## <a name="remarks"></a>備註
 此介面可讓運算式評估工具表示剖析樹狀結構中的函數。 `Create`這個介面中的方法是用來建立代表方法之輸入參數的物件。 然後藉由呼叫 [評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) 方法來執行函式，此方法會傳回表示函式傳回值的物件。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
