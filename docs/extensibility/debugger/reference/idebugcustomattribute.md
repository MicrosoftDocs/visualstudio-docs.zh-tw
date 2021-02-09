---
title: IDebugCustomAttribute |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1baa46cd9be53134d42c71e8c2bd88e3e2c38d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907959"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
這個介面代表自訂屬性，它可以提供屬性的名稱、父系和類別類型。

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會執行這個介面，以支援與符號相關聯的自訂屬性。 它通常會在本身的物件上執行。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) 會傳回這個介面。 呼叫 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 方法會傳回 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugCustomAttribute` 。

|方法|描述|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|取得附加目前屬性的欄位。|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|取得自訂屬性類別類型。|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|取得自訂屬性的名稱。|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|取得以位元組 blob 表示的屬性資訊。|

## <a name="remarks"></a>備註
 自訂屬性是 c # 的結構，可提供與特定類別或方法相關聯的自訂中繼資料。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
