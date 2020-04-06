---
title: IDebugBreakpoint決議2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734743"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
此介面表示描述綁定斷點的資訊。

## <a name="syntax"></a>語法

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 除錯引擎 (DE) 實現此介面作為其對斷點的支援的一部分。 此介面提供工作階段調試管理器在使用者查看斷點屬性時使用的綁定斷點的說明。

## <a name="notes-for-callers"></a>通話備註
 對[GetBreakpoint 解析的](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)調用將返回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointResolution2`。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|獲取此解析度表示的斷點的類型。|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|獲取描述此斷點的斷點解析資訊。|

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
