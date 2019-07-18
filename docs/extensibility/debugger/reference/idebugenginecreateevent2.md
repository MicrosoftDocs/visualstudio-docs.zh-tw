---
title: IDebugEngineCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 088de1540a07e85bfb474308987302d8a7c613ba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352452"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
偵錯引擎 (DE) 會將此介面傳送至工作階段的偵錯管理員 (SDM) 中，建立的預設執行個體時。

## <a name="syntax"></a>語法

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 DE 會實作這個介面做為其正常作業的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面的相同物件上 (使用 SDM`QueryInterface`方法來存取`IDebugEvent2`介面)。

## <a name="notes-for-callers"></a>呼叫端資訊
 DE 會建立並 DE 具現化時，會傳送這個事件的物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugEngineCreateEvent2`。

|方法|描述|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|擷取物件，表示新建立的偵錯引擎 (DE)。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)