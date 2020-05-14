---
title: IDebug自定義屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732686"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
此介面表示自定義屬性,它可以提供屬性的名稱、父級和類類型。

## <a name="syntax"></a>語法

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 符號提供程式實現此介面以支援與符號關聯的自定義屬性。 它通常在其自己的對象上實現。

## <a name="notes-for-callers"></a>通話備註
 對[Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)的調用將返回此介面。 對[Enum](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)的呼叫的[IEnumDebug 自訂屬性介面](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugCustomAttribute`。

|方法|描述|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|取得目前的屬性附加到的欄位。|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|獲取自定義屬性類類型。|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|獲取自定義屬性的名稱。|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|將屬性資訊作為位元組 Blob 獲取。|

## <a name="remarks"></a>備註
 自定義屬性是提供與特定類或方法關聯的自定義元數據的 C# 結構。

## <a name="requirements"></a>需求
 標題: sh.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Symbol Provider Interfaces](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
