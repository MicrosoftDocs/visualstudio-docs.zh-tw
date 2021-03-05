---
description: 判斷這個欄位的自訂屬性是否存在，如果存在，則傳回屬性資訊。
title: IDebugCustomAttributeQuery2 |Microsoft 檔
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 62461cbdbfe373f6c3d45569564e611efdd6f452
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160221"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
判斷這個欄位的自訂屬性是否存在，如果存在，則傳回屬性資訊。

## <a name="syntax"></a>Syntax

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 符號提供者會在執行 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 的相同物件上執行這個介面，以便支援自訂屬性。

## <a name="notes-for-callers"></a>呼叫者注意事項
 使用 [QueryInterface](/cpp/atl/queryinterface) 從 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面取得這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示 **IDebugCustomAttributeQuery** 介面的方法。

|方法|描述|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|判斷自訂屬性是否以名稱存在。|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|取得指定之自訂屬性的屬性資訊。|

 除了 **IDebugCustomAttributeQuery** 方法之外，還會 `IDebugCustomAttributeQuery2` 執行下列方法：

|方法|描述|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|取得附加至此欄位之所有自訂屬性的列舉值。|

## <a name="remarks"></a>備註
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)方法可以傳回針對此欄位所定義的所有自訂屬性的列舉值。

## <a name="requirements"></a>規格需求
 標頭： sh. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
