---
description: 這個介面代表陣列物件。
title: IDebugArrayObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e27f40a3f8a54c9cda285ba30bdcbc53472aab59
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078106"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面代表陣列物件。

## <a name="syntax"></a>Syntax

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行此介面來代表陣列。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果物件代表陣列， [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面可以使用 [QueryInterface](/cpp/atl/queryinterface) 來取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了介面上的方法之外 `IDebugObject` ，下列方法也會在介面上執行 `IDebugArrayObject` 。

|方法|描述|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|取得陣列中的元素計數。|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|取得陣列的元素。|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|取得陣列的所有元素。|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|取得陣列的順位。|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|取得陣列的維度。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來表示剖析樹狀結構中的陣列。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
