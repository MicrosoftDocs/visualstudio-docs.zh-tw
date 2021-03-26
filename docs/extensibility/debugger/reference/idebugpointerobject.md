---
description: 此介面代表指標物件。
title: IDebugPointerObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af6b8f6022a9363eb5391d6f0519603fa48668c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087596"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面代表指標物件。

## <a name="syntax"></a>Syntax

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行這個介面來表示指標物件。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果代表指標， [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面可以使用 [QueryInterface](/cpp/atl/queryinterface) 來取得這個介面 `IDebugObject` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)的方法之外，介面也會 `IDebugPointerObject` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|取得介面指向的物件。|
|[GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|取得介面指向一系列連續位元組的值。|
|[SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|設定介面指向一系列連續位元組的值。|

## <a name="remarks"></a>備註
 運算式評估工具會使用此介面來表示剖析樹狀結構中的指標。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
