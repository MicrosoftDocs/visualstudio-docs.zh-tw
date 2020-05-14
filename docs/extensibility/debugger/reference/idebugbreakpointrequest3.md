---
title: IDebug 突破點請求3 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734826"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
此介面表示創建和綁定任何類型的斷點所需的資訊。 它是[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)的副檔名。

## <a name="syntax"></a>語法

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>實施者說明
 會話調試管理員 (SDM) 通常實現此介面。

## <a name="notes-for-callers"></a>通話備註
 除錯引擎 (DE) 透過 IDebugBreakpointRequest2 介面上調用在呼叫[創建掛起斷點](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)時收到的[查詢介面](/cpp/atl/queryinterface)來存取此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 除了從[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)繼承的方法`IDebugBreakpointRequest3`外, 介面還公開了以下方法。

|方法|描述|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|獲取描述此斷點請求的斷點請求資訊。|

## <a name="remarks"></a>備註
 此介面用於通過[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構向DE提供其他資訊。 此附加資訊包括 DE 的供應商 ID(以 GUID 形式)、追蹤點的名稱和斷點約束的名稱。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
