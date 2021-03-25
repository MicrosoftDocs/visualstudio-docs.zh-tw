---
description: 此介面描述方法。
title: IDebugMethodField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5234f209ecd8866c8fa55735ad21a79cdfd7404d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054318"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
此介面描述方法。

## <a name="syntax"></a>Syntax

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會在執行 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 介面的相同物件上，執行這個介面。 此介面是提供方法的特製化。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回，請使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面取得這個介面 `FIELD_TYPE_METHOD` 。 此外，方法（ [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)、 [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)和 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)）都會傳回 `IDebugMethodField` 介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|建立方法參數的列舉值。|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|取得包含方法之物件的 "this" 指標。|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|針對方法的所有區域變數建立枚舉器。|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|為方法的選取區域變數建立枚舉器。|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|判斷是否已定義特定的自訂屬性。|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|建立方法之靜態區域變數的列舉值。|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|取得方法的全域容器。|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|針對呼叫方法所需的每個引數，建立其類型的列舉值。|

## <a name="remarks"></a>備註
 方法可以包含參數和本機變數。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
