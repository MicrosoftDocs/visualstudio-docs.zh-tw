---
title: IDebugEventCallback2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 68d29d928f310cb045ed712a151f9275446465a4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116200"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
偵錯引擎 (DE) 會使用此介面，將偵錯事件傳送至工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 實作這個介面來接收事件，從 偵錯引擎。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 偵錯引擎通常會接收這個介面，當呼叫 SDM[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)，[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。 偵錯引擎將事件傳送到 SDM 藉由呼叫[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEventCallback2`。  
  
|方法|描述|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|傳送通知的偵錯 SDM 的事件。|  
  
## <a name="remarks"></a>備註  
 雖然[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)指定它們需要`IDebugEventCallback2`介面，這不是大小寫，而且介面指標將永遠為 null 值。 反之，必須使用的偵錯引擎`IDebugEventCallback2`介面的呼叫中收到[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)，[附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)，或[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)。  
  
 如果封裝實作[IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md)在 managed 程式碼，強烈建議，<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>傳遞至各種介面上叫用[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)