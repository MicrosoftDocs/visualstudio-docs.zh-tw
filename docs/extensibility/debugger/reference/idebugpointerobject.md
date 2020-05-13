---
title: IDebugPointer物件 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject
helpviewer_keywords:
- IDebugPointerObject interface
ms.assetid: 257fa167-b46e-4ffb-9a12-272efbf26702
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b28189b3f0a07a27f5e4478f64963a63d634db5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725485"
---
# <a name="idebugpointerobject"></a>IDebugPointerObject
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面表示指針對象。

## <a name="syntax"></a>語法

```
IDebugPointerObject : IDebugObject
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以表示指針對象。

## <a name="notes-for-callers"></a>通話備註
 如果表示指標,`IDebugObject`則[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以使用[查詢介面](/cpp/atl/queryinterface)獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)繼承的方法`IDebugPointerObject`外, 介面還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[Dereference](../../../extensibility/debugger/reference/idebugpointerobject-dereference.md)|獲取介面指向的物件。|
|[取得位元組](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)|獲取介面指向的值,作為一系列連續位元組。|
|[設定位元組](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)|設置介面從一系列連續位元組指向的值。|

## <a name="remarks"></a>備註
 表達式賦值器使用此介面表示解析樹中的指標。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
