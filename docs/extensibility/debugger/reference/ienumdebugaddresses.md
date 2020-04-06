---
title: IEnum調試位址 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717593"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
此介面表示實現[IDebugAddress 介面](../../../extensibility/debugger/reference/idebugaddress.md)的物件的集合。

## <a name="syntax"></a>語法

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由符號提供程式實現,以提供實現[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)介面的物件集。 請注意,由於[存在GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)方法,這不是標準COM枚舉。

## <a name="notes-for-callers"></a>通話備註
 此介面由[從上下文獲取位址](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)和[從位置獲取位址](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)返回。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面實現以下方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|從枚舉中檢索下一組[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。|
|[跳](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|跳過指定數量的條目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|將枚舉重置為第一個條目。|
|[複製](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|檢索當前枚舉的副本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|檢索枚舉中的條目數。|

## <a name="remarks"></a>備註
 調試引擎通常使用此介面來幫助確定要向表達式賦值器提供的適當位址。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
