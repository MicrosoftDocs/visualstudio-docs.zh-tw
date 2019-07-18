---
title: IDebugArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be1f65e3814cbd88d32a63169234a42f76db4e6d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337578"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面會表示陣列物件。

## <a name="syntax"></a>語法

```
IDebugArrayObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面來代表陣列。

## <a name="notes-for-callers"></a>呼叫端資訊
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用，取得這個介面[QueryInterface](/cpp/atl/queryinterface)如果物件表示的陣列。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 上的方法除了`IDebugObject`介面上實作下列方法`IDebugArrayObject`介面。

|方法|描述|
|------------|-----------------|
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|取得陣列中的項目數目。|
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|取得陣列的項目。|
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|取得陣列的所有項目。|
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|取得陣列的陣序規範。|
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|取得陣列維度。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來代表剖析樹狀結構中的陣列。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)