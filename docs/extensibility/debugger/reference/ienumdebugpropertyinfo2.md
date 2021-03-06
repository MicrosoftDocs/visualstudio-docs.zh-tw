---
description: 此介面會列舉 DEBUG_PROPERTY_INFO 結構。
title: IEnumDebugPropertyInfo2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2
helpviewer_keywords:
- IEnumDebugPropertyInfo2
ms.assetid: fdea8262-40b8-473e-88ba-639e4c4648e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fea2dc5cf958f87463af9dfca9f29bec5d01a82b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224183"
---
# <a name="ienumdebugpropertyinfo2"></a>IEnumDebugPropertyInfo2
此介面會列舉 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構。

## <a name="syntax"></a>Syntax

```
IEnumDebugPropertyInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Debug engine (DE) 會執行這個介面，以代表特定屬性的資訊。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 以取得這個介面，此介面代表特定屬性的子系。 呼叫 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 以取得這個介面，此介面代表特定堆疊框架的屬性。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IEnumDebugPropertyInfo2` 。

|方法|描述|
|------------|-----------------|
|[下一步](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md)|抓取列舉序列中指定數目的 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構。|
|[Skip](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-skip.md)|略過列舉序列中指定數目的 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構。|
|[重設](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-reset.md)|將列舉順序重設為開頭。|
|[複製](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-clone.md)|建立包含與目前列舉值相同列舉狀態的列舉值。|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)|取得枚舉器中 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構的數目。|

## <a name="remarks"></a>備註
 一般情況下，屬性（property）是可包含名稱、值、位址和類型的資訊階層，以及任何適用于關聯屬性物件或堆疊框架的其他資訊。 如需詳細資訊，請參閱 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
