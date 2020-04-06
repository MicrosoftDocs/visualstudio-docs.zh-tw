---
title: 事件屬性 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVENTATTRIBUTES
helpviewer_keywords:
- EVENTATTRIBUTES enumeration
ms.assetid: 04db10f7-df31-4464-98e8-b3777428179e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c479058a5e6abb61fb419425706d2a8b26858d04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737055"
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

## <a name="fields"></a>欄位
`EVENT_ASYNCHRONOUS`\
指示事件是異步的,不需要對該事件進行回復。

`EVENT_SYNCHRONOUS`\
指示事件是同步的;通過[「繼續從同步事件](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)」進行回覆。

`EVENT_STOPPING`\
指示這是停止事件。 必須與或`EVENT_ASYNCHRONOUS``EVENT_SYNCHRONOUS`合併。

`EVENT_ASYNC_STOP`\
指示非同步停止事件。 目前沒有此類事件。 此標誌僅是占位符。

`EVENT_SYNC_STOP`\
指示同步停止事件(和`EVENT_SYNCHRONOUS``EVENT_STOPPING`的組合)。 當調試引擎 (DE) 傳送停止事件時,將使用此值。 答覆是透過呼叫[執行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)、[步驟](../../../extensibility/debugger/reference/idebugprogram2-step.md)或[繼續](../../../extensibility/debugger/reference/idebugprogram2-continue.md)。

`EVENT_IMMEDIATE`\
指示立即同步發送到 IDE 的事件。 此標誌與其他標誌(如`EVENT_ASYNCHRONOUS``EVENT_SYNCHRONOUS`,)`EVENT_SYNC_STOP`結合 使用,或指示事件的類型以及已知答覆機制(如果有)的事實。

`EVENT_EXPRESSION_EVALUATION`\
該事件是表達式計算的結果。

## <a name="remarks"></a>備註
這些值在[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法的`dwAttrib`參數中傳遞。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)
- [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
