---
title: IDebugBoundBreakpoint2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a37f637e77c342b3af977884241d0e922ac6aaa6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
此介面代表中斷點繫結至程式碼位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)建立此介面。 呼叫[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)和[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)也可以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBoundBreakpoint2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得從中建立指定的繫結的中斷點暫止中斷點。|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得這個繫結中斷點的狀態。|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|取得這個繫結中斷點目前叫用的次數。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述此中斷點的中斷點解析度。|  
|[啟用](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|設定此繫結中斷點的叫用的次數。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設定或變更與此繫結中斷點相關聯的條件。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|設定或變更與此繫結中斷點相關聯的密碼計數。|  
|[刪除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除中斷點。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)