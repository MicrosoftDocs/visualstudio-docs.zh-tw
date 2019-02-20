---
title: EVENTATTRIBUTES | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b0f7de41857984464afb1576448fec56bd2841d
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2019
ms.locfileid: "56413263"
---
# <a name="eventattributes"></a>EVENTATTRIBUTES
指定事件屬性。

## <a name="syntax"></a>語法

```cpp
enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
typedef DWORD EVENTATTRIBUTES;
```

```csharp
public enum enum_EVENTATTRIBUTES {
    EVENT_ASYNCHRONOUS          = 0x0000,
    EVENT_SYNCHRONOUS           = 0x0001,
    EVENT_STOPPING              = 0x0002,
    EVENT_ASYNC_STOP            = 0x0002,
    EVENT_SYNC_STOP             = 0x0003,
    EVENT_IMMEDIATE             = 0x0004,
    EVENT_EXPRESSION_EVALUATION = 0x0008
};
```

## <a name="members"></a>成員
EVENT_ASYNCHRONOUS  
表示事件是非同步，而且需要事件未得到回覆。

EVENT_SYNCHRONOUS  
指出事件是同步的藉由回覆[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)。

EVENT_STOPPING  
指出這是停止事件。 必須與其中一個結合`EVENT_ASYNCHRONOUS`或`EVENT_SYNCHRONOUS`。

EVENT_ASYNC_STOP  
表示非同步停止事件。 目前沒有任何這類事件。 這個旗標是只是預留位置。

EVENT_SYNC_STOP  
表示同步停止事件 (的組合`EVENT_SYNCHRONOUS`和`EVENT_STOPPING`)。 傳送 「 停止 」 事件時，偵錯引擎 (DE) 會使用此值。 回覆會透過呼叫[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)，[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)，或[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。

EVENT_IMMEDIATE  
表示會立即和同步地傳送到 IDE 事件。 這個旗標會結合其他旗標，像是`EVENT_ASYNCHRONOUS`， `EVENT_SYNCHRONOUS`，或`EVENT_SYNC_STOP`來表示事件以及 （如果有的話） 的回覆機制已知的事實類型。

EVENT_EXPRESSION_EVALUATION  
事件是運算式評估的結果。

## <a name="remarks"></a>備註
這些值會傳遞`dwAttrib`的參數[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。

這些值可能會合併的位元`OR`。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
[列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)  
[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
