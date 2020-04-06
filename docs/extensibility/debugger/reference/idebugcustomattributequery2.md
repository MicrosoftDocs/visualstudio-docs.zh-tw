---
title: IDebug自定義屬性查詢2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fe3969002c64ab361de76012c432e2bb5c61b5c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732484"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
確定此欄位的自定義屬性的存在,如果存在,則返回屬性資訊。

## <a name="syntax"></a>語法

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式在實現[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)的同一對象上實現此介面,以支援自定義屬性。

## <a name="notes-for-callers"></a>通話備註
 使用[查詢介面](/cpp/atl/queryinterface)從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面獲取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示了**IDebugCustom 屬性查詢**介面的方法。

|方法|描述|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|確定自定義屬性是否存在名稱。|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|獲取給定自定義屬性的屬性資訊。|

 除了**IDebugCustom 屬性查詢**`IDebugCustomAttributeQuery2`方法之外, 實現以下方法:

|方法|描述|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|獲取附加到此欄位的所有自定義屬性的枚舉器。|

## <a name="remarks"></a>備註
 [IEnumDebugCustom Attributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)方法可以為此欄位定義的所有自定義屬性返回枚舉器。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
