---
title: IDebugPropertyCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31764e62f53304d30305f8326c6ab887ffa69e53
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65457458"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
這個介面會傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 建立與特定文件相關聯的屬性時。

## <a name="syntax"></a>語法

```
IDebugPropertyCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面來報告已建立的屬性。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上。 使用 SDM [QueryInterface](/cpp/atl/queryinterface)若要存取`IDebugEvent2`介面。 如果 DE 已建立的已載入或建立的指令碼相關聯的屬性，而且該指令碼必須出現在 IDE 中，會實作這個介面。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 建立，並將此事件的物件傳送至已建立屬性的報表。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至正在進行偵錯程式時，會將 SDM 所提供的回呼函式。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugPropertyCreateEvent2`介面。

|方法|描述|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|取得新的屬性。|

## <a name="remarks"></a>備註
 如果屬性的特定文件或與其相關聯的指令碼，DE 可以傳送這個事件以 SDM 以更新**指令碼文件**視窗與文件的名稱。 會呼叫 SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)搭配引數`guidDocument`擷取`VARIANT`包含[IUnknown](/cpp/atl/iunknown)指標。 會呼叫 SDM [QueryInterface](/cpp/atl/queryinterface)來擷取此指標上[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)介面，用來更新**指令碼文件**視窗。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)