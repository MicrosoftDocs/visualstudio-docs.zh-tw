---
title: IEnumDebugFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50d80242ca516c5fa7f3ad297250e25c782664d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350373"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
此介面代表實作的物件的集合[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。

## <a name="syntax"></a>語法

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 符號提供者來提供實作的物件組實作這個介面[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。 請注意，這不是標準的 COM 列舉的緣故[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)方法。

## <a name="notes-for-callers"></a>呼叫端資訊
 這個介面由[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)並[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 這個介面會實作下列方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|擷取下的一組[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)列舉中的物件。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|略過指定的數目的項目。|
|[Reset](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|將列舉重設第一個項目中。|
|[Clone](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|擷取一份目前的列舉型別。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|擷取列舉中的項目數。|

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標頭： sh.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)