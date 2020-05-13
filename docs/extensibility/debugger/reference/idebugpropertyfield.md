---
title: IDebug屬性欄位 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField
helpviewer_keywords:
- IDebugPropertyField interface
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96a3f3c2dca16cd2c28c9d1727e4ac145c91c482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720692"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
此介面提供允許獲取和設置屬性的功能。

## <a name="syntax"></a>語法

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)的同一對象上實現此介面。 此介面是支援類上屬性概念的專門化。

## <a name="notes-for-callers"></a>通話備註
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_KIND_PROP`方法返回 ,則使用[查詢介面](/cpp/atl/queryinterface)從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)和[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面上的方法外,此介面還實現了以下方法:

|方法|描述|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|獲取獲取屬性的方法。|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|獲取設置屬性的方法。|

## <a name="remarks"></a>備註
 屬性是託管代碼概念,表示被視為變數的方法。 屬性在非託管C++中不存在。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
