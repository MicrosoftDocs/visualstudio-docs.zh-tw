---
title: IDebugPointerObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac28cc208818527e1630aa7a2d5280165a5ffc5a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719284"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面表示的指標物件。

## <a name="syntax"></a>語法

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面來表示的指標物件。

## <a name="notes-for-callers"></a>呼叫端資訊
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用，取得這個介面[QueryInterface](/cpp/atl/queryinterface)如果`IDebugObject`表示的指標。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自方法[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)，則`IDebugPointerObject`介面會公開下列方法。

|方法|描述|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|取得介面所指向的物件。|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|取得做為一系列的連續位元組介面指向的值。|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|設定從一系列的連續位元組介面指向的值。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來代表剖析樹狀結構中的指標。

## <a name="requirements"></a>需求
 標頭： ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)