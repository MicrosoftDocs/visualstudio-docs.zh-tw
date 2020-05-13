---
title: IEnumDebug屬性資訊2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bfa0f8feff6a53b84a6337e5bea8bdc622e19a20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715346"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
此介面枚舉[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。

## <a name="syntax"></a>語法

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面以表示特定屬性的資訊。

## <a name="notes-for-callers"></a>通話備註
 調用[Enum 兒童](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)以獲取表示特定屬性的子級的此介面。 調用[Enum 屬性](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)以獲取表示特定堆疊幀屬性的此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IEnumDebugPropertyInfo2`。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|檢索枚舉序列中指定數量的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。|
|[跳](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|在枚舉序列中跳過指定數量的[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構。|
|[重設](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|將枚舉序列重置為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|建立與當前枚舉器相同的枚舉狀態的枚舉器。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|獲取枚舉器中[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構的數量。|

## <a name="remarks"></a>備註
 通常,屬性是一個資訊層次結構,可以包含名稱、值、位址和類型,以及適用於關聯的屬性物件或堆疊幀的任何其他資訊。 有關詳細資訊[,請參閱 IDebugProperty2。](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
