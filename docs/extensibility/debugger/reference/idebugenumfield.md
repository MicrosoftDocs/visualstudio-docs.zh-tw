---
title: IDebugEnumField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField
helpviewer_keywords:
- IDebugEnumField interface
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a67c660ec8457191e688fdd430c3f7a07b5d75c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933319"
---
# <a name="idebugenumfield"></a>IDebugEnumField
這個介面代表列舉型別。

## <a name="syntax"></a>Syntax

```
IDebugEnumField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會執行此介面來代表列舉。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回，請使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面取得這個介面 `FIELD_TYPE_ENUM` 。

## <a name="methods-in-vtable-order"></a>採用 VTable 順序的方法
 除了和介面上的方法 `IDebugField` `IDebugContainerField` ，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|傳回描述此列舉型別名稱的 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 。|
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|傳回與指定值相關聯之列舉常數的名稱。|
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|傳回與指定的列舉常數名稱相關聯的值。|
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|傳回與指定的列舉常數名稱相關聯的值，但忽略大小寫。|

## <a name="remarks"></a>備註
 它是實際系結至具有系結之位置的基礎[符號。](../../../extensibility/debugger/reference/idebugbinder-bind.md)

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [綁定](../../../extensibility/debugger/reference/idebugbinder-bind.md)
