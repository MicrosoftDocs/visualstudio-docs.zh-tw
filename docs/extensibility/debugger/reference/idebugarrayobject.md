---
title: IDebugarray物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 709273b89d89759163acb725220d1092d33ad72f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736222"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示陣列物件。

## <a name="syntax"></a>語法

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以表示陣列。

## <a name="notes-for-callers"></a>通話備註
 如果物件表示陣列,[則 IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用[查詢介面](/cpp/atl/queryinterface)獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了`IDebugObject`介面上的方法外,在`IDebugArrayObject`介面上實現了以下方法。

|方法|描述|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|獲取陣列中元素的計數。|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|獲取陣列的元素。|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|獲取陣列的所有元素。|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|獲取陣列的排名。|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|獲取陣列的尺寸。|

## <a name="remarks"></a>備註
 表達式賦值器使用此介面表示解析樹中的陣列。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
