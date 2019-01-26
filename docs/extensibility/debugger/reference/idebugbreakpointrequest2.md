---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e61b89fb889a2e274c482e083610b97a19f57f5c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001978"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
這個介面會表示建立並繫結任何中斷點類型的所需的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 工作階段的偵錯管理員 (SDM) 通常會實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 偵錯引擎 (DE) 會接收這個介面，透過呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)才能建立暫止中斷點。 呼叫[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)可以將此介面擷取 DE。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBreakpointRequest2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|取得此中斷點要求的中斷點位置類型。|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|取得描述此中斷點要求的中斷點要求資訊。|  
  
## <a name="remarks"></a>備註  
 之後的程式進行偵錯已載入，呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)會暫止中斷點繫結到程式中要求的位置。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)