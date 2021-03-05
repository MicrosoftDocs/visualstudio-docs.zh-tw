---
description: IDebugBreakpointRequest3 介面代表建立及系結任何中斷點類型所需的資訊。
title: IDebugBreakpointRequest3 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 628a68cf6712e6863550d85a5f876afbe1b6bdb5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150740"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
此介面代表建立和系結任何類型中斷點所需的資訊。 它是 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)的延伸模組。

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 會話 debug manager (SDM) 通常會執行這個介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
 Debug engine (DE) 存取這個介面，方法是在呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)時所收到的 IDebugBreakpointRequest2 介面上呼叫[QueryInterface](/cpp/atl/queryinterface) 。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了繼承自 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)的方法之外，介面也會 `IDebugBreakpointRequest3` 公開下列方法。

|方法|描述|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|取得描述此中斷點要求的中斷點要求資訊。|

## <a name="remarks"></a>備註
 這個介面是用來提供其他資訊給 DE [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構。 這項額外的資訊包括「DE 的廠商識別碼」 (格式為 GUID) 、追蹤點的名稱，以及中斷點條件約束的名稱。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
