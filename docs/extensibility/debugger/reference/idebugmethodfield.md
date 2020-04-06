---
title: IDebugMethodfield |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061035933e57ea4ca8e7857f68ac3d6311bae32c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727069"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
此介面描述方法。

## <a name="syntax"></a>語法

```
IDebugMethodField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面的同一對象上實現此介面。 此介面是一個專門化,它提供了一個方法。

## <a name="notes-for-callers"></a>通話備註
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_METHOD`,請使用[查詢介面](/cpp/atl/queryinterface)從[IDebug 容器欄位](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面獲取此介面。 此外,方法[,GetPropertyGetter,GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)和[枚舉構建器](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)`IDebugMethodField`,[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)都返回介面 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|為方法的參數創建枚舉器。|
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|取得包含方法的物件的"this"指標。|
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|為方法的所有局部變數創建枚舉器。|
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|為方法的選定局部變數創建枚舉器。|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|確定是否已定義特定的自定義屬性。|
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|為方法的靜態局部變數創建枚舉器。|
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|獲取 方法的全域容器。|
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|為調用方法所需的每個參數的類型創建枚舉器。|

## <a name="remarks"></a>備註
 方法可以包含參數和局部變數。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
