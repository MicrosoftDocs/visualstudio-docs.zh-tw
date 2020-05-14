---
title: IDebug函數物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject
helpviewer_keywords:
- IDebugFunctionObject interface
ms.assetid: 8d94e97c-a9d1-400c-8a98-a44b5385b33a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6433c1f2c540b040a3b3beccc264377e69592387
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728497"
---
# <a name="idebugfunctionobject"></a>IDebugFunctionObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示函數。

## <a name="syntax"></a>語法

```
IDebugFunctionObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以表示函數。

## <a name="notes-for-callers"></a>通話備註
 此介面是[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面的專門化,使用介面上的`IDebugObject`[查詢介面](/cpp/atl/queryinterface)獲得。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)繼承的方法`IDebugFunctionObject`外, 介面還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)|創建基元數據物件。|
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject-createobject.md)|使用構造函數創建物件。|
|[CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)|創建沒有構造函數的物件。|
|[CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)|創建陣列物件。|
|[CreateStringObject](../../../extensibility/debugger/reference/idebugfunctionobject-createstringobject.md)|建立字串物件。|
|[評價](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)|調用函數並將結果值作為物件返回。|

## <a name="remarks"></a>備註
 此介面使表達式賦值器能夠表示解析樹中的函數。 此`Create`介面中的方法用於建構表示方法的輸入參數的物件。 然後,可以通過調用[評估](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)方法來執行該函數,該方法返回表示函數返回值的物件。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
