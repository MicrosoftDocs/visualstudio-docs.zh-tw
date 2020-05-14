---
title: IDebug 突破點綁定事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735305"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
此介面告訴工作階段調試管理器 (SDM), 掛起的斷點已成功綁定到載入的程式。

## <a name="syntax"></a>語法

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面作為其對斷點的支援的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當掛起的斷點成功綁定到正在調試的程式時,DE 將創建併發送此事件物件。 該事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointBoundEvent2`。

|方法|描述|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|獲取正在綁定的掛起斷點。|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|創建在此事件中綁定的斷點枚舉器。|

## <a name="remarks"></a>備註
 每當綁定斷點時,事件都會發送到 SDM。 如果斷點無法綁定,則發送[IDebugBreakpointErrorEvent2;如果斷點無法綁定,則發送 IDebugBreakpointErrorEvent2;](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)否則,將`IDebugBreakpointBoundEvent2`傳送 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
