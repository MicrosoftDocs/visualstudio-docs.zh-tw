---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4884da23d3be45067884c295f80305683cb16abb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352851"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
此介面代表可描述繫結的中斷點的資訊。

## <a name="syntax"></a>語法

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。 這個介面提供的繫結的中斷點，在使用者檢視中斷點的屬性時，會使用工作階段的偵錯管理員的描述。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)傳回此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointResolution2`。

|方法|描述|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|取得由這個解決方案的中斷點類型。|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|取得描述此中斷點的中斷點解析資訊。|

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)