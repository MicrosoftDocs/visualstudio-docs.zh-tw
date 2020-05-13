---
title: IDebugBreakpoint請求2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734911"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
此介面表示創建和綁定任何類型的斷點所需的資訊。

## <a name="syntax"></a>語法

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 會話調試管理員 (SDM) 通常實現此介面。

## <a name="notes-for-callers"></a>通話備註
 調試引擎 (DE) 通過調用[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)接收此介面,以創建掛起的斷點。 對[GetBreakpoint 請求的](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)調用可以從 DE 檢索此介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下表顯示的方法`IDebugBreakpointRequest2`。

|方法|描述|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|獲取此斷點請求的斷點位置類型。|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|獲取描述此斷點請求的斷點請求資訊。|

## <a name="remarks"></a>備註
 載入正在除錯的程式後,對[Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)的調用將掛起的斷點綁定到程式中的請求位置。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
