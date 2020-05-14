---
title: IEnum調試場 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716776"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
此介面表示實現[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面的物件的集合。

## <a name="syntax"></a>語法

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 此介面由符號提供程式實現,以提供實現[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面的物件集。 請注意,由於[存在GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)方法,這不是標準COM枚舉。

## <a name="notes-for-callers"></a>通話備註
 此介面由[GetMethodFieldsBy名稱](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)和[獲取名稱空間已使用At位址](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)返回。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 此介面實現以下方法。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|從枚舉中檢索下一組[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。|
|[跳](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|跳過指定數量的條目。|
|[重設](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|將枚舉重置為第一個條目。|
|[複製](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|檢索當前枚舉的副本。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|檢索枚舉中的條目數。|

## <a name="remarks"></a>備註

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
