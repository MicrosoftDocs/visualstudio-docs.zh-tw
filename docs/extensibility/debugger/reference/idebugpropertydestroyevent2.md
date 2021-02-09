---
title: IDebugPropertyDestroyEvent2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b09fb8c644adb5464519f0f30bd8deff0be821ba
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900089"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
當與特定檔相關聯的屬性即將終結時，debug engine 會將這個介面傳送 (DE) 至會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 DE 會執行這個介面，以報告屬性已終結。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與這個介面相同的物件上執行。 SDM 會使用 [QueryInterface](/cpp/atl/queryinterface) 來存取 `IDebugEvent2` 介面。 如果 DE 先前已建立與腳本相關聯的屬性，就會執行這個介面;終結屬性會從 IDE 移除相關聯的腳本。

## <a name="notes-for-callers"></a>呼叫者注意事項
 「取消」會建立並傳送此事件物件，以報告屬性已損毀。 使用 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送事件，該函式會在附加至要進行偵錯工具的程式時提供。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugPropertyDestroyEvent2` 。

|方法|描述|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|取得要終結的屬性。|

## <a name="remarks"></a>備註
 如需有關使用這些事件之原因的詳細資訊，請參閱 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) 的備註。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
