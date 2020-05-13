---
title: IDebugEvent2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729905"
---
# <a name="idebugevent2"></a>IDebugEvent2
此介面用於通訊關鍵調試資訊(如斷點停止)和非關鍵資訊(如調試消息)。

## <a name="syntax"></a>語法

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 和自訂埠供應商在與所有其他事件介面相同的物件上實現此介面。

## <a name="notes-for-callers"></a>通話備註
 使用提供給[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)或[事件的](../../../extensibility/debugger/reference/idebugportevents2-event.md)介面ID (IID) 參數,會話調試管理器 (SDM) 調用`IDebugEvent2`介面上的[QueryInterface](/cpp/atl/queryinterface)以獲取適當的事件介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEvent2`。

|方法|描述|
|------------|-----------------|
|[取得屬性](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|獲取此調試事件的屬性。|

## <a name="remarks"></a>備註
 更具體的事件介面(如[IDebugBreakpointEvent2)](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)不派生自IDebugEvent2介面,而是作為與`IDebugEvent2`的相同物件上的單獨介面實現。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
