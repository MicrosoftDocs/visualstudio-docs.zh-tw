---
title: IDebug 突破點錯誤事件2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735051"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
此介面告訴工作階段調試管理員 (SDM),由於警告或錯誤,無法將掛起的斷點綁定到載入的程式。

## <a name="syntax"></a>語法

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 DE 實現此介面作為其對斷點的支援的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的對象上實現(SDM 使用`IDebugEvent2`[查詢介面](/cpp/atl/queryinterface)存取介面)。

## <a name="notes-for-callers"></a>通話備註
 當掛起的斷點無法綁定到正在調試的程式時,DE 將創建併發送此事件物件。 該事件使用 SDM 提供的[IDebugEvent 回調2](../../../extensibility/debugger/reference/idebugeventcallback2.md)回檔功能在附加到正在調試的程式時發送。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointErrorEvent2`。

|方法|描述|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|獲取描述警告或錯誤的[IDebugErrorBreakpointpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)介面。|

## <a name="remarks"></a>備註
 每當綁定斷點時,事件都會發送到 SDM。 如果斷點無法結合,則傳送`IDebugBreakpointErrorEvent2`。否則,將發送[IDebugBreakpoint 綁定事件 2。](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)

 例如,當與掛起斷點關聯的條件無法解析或計算時,將發送一條警告,指出此時無法綁定掛起的斷點。 如果斷點的代碼尚未載入,則可能發生此情況。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
