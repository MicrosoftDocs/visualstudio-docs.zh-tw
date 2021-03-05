---
description: IDebugBreakPointRequest2 介面代表建立及系結任何中斷點類型所需的資訊。
title: IDebugBreakpointRequest2 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e7d13c945de1358265a5eb92769192ce736be49
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162351"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
此介面代表建立和系結任何類型中斷點所需的資訊。

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 會話 debug manager (SDM) 通常會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 Debug engine (DE) 透過呼叫 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) 接收這個介面，以便建立暫止中斷點。 呼叫 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) 可以從 DE 取出這個介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法 `IDebugBreakpointRequest2` 。

|方法|描述|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|取得此中斷點要求的中斷點位置型別。|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|取得描述此中斷點要求的中斷點要求資訊。|

## <a name="remarks"></a>備註
 在 [載入要進行](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 偵錯工具的程式之後，呼叫系結會將暫止中斷點系結至程式中要求的位置。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
