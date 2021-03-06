---
description: 這個介面代表執行 IDebugAddress 介面的物件集合。
title: IEnumDebugAddresses |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ea9e4115c1664e1dcd05041f7ece056b5de01dae
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222636"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
這個介面代表執行 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的物件集合。

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 這個介面是由符號提供者所執行，以提供可執行 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 介面的物件集合。 請注意，這不是標準的 COM 列舉，因為 [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) 方法是否存在。

## <a name="notes-for-callers"></a>呼叫者注意事項
 [GetAddressesFromCoNtext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)和[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)會傳回這個介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 這個介面會實作為下列方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|從列舉中抓取下一組 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|略過指定數目的專案。|
|[重設](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|將列舉重設為第一個專案。|
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|抓取目前列舉的複本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|捕獲列舉中的專案數。|

## <a name="remarks"></a>備註
 這個介面通常會由 debug 引擎用來協助判斷要提供給運算式評估工具的適當位址。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
