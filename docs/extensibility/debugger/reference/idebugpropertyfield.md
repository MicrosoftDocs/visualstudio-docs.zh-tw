---
title: IDebugPropertyField |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720692"
---
# <a name="idebugpropertyfield"></a>IDebugPropertyField
這個介面會提供可讓您取得和設定屬性的功能。

## <a name="syntax"></a>語法

```
IDebugPropertyField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會在執行 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)的相同物件上，執行這個介面。 這個介面是一個特製化，可支援類別上的屬性概念。

## <a name="notes-for-callers"></a>呼叫者注意事項
 如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法傳回，請使用[QueryInterface](/cpp/atl/queryinterface)從[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面取得這個介面 `FIELD_KIND_PROP` 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 和 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 介面上的方法，這個介面也會執行下列方法：

|方法|描述|
|------------|-----------------|
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|取得取得屬性的方法。|
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|取得設定屬性的方法。|

## <a name="remarks"></a>備註
 屬性是 managed 程式碼的概念，並代表視為變數的方法。 屬性不存在於非受控 c + + 中。

## <a name="requirements"></a>需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
