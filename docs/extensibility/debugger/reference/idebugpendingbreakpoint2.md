---
title: IDebugPendingBreakpoint2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5e84180747a3e6a3b9e5a34e7694f4cd07867c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
這個介面表示中斷點已就緒可繫結至程式碼位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)建立從暫止中斷點[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面。 呼叫[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)建立`IDebugBreakpoint2`表示繫結的中斷點在程式中的介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPendingBreakpoint2`。  
  
|方法|描述|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|決定是否此暫止中斷點可以繫結至程式碼位置。|  
|[繫結](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|將這個暫止中斷點繫結到一或多個程式碼位置。|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|取得這個暫止中斷點的狀態。|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|取得用來建立這個暫止中斷點的中斷點要求。|  
|[虛擬化](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|切換這個暫止中斷點虛擬化的狀態。|  
|[啟用](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|切換這個暫止中斷點的啟用的狀態。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設定或變更暫止中斷點與此相關聯的條件。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設定或變更與這個暫止中斷點相關聯的傳遞計數。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|列舉從這個暫止中斷點繫結的所有中斷點。|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|列舉導致這個暫止中斷點的所有錯誤中斷點。|  
|[刪除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|刪除這個暫止中斷點，並從其繫結的所有中斷點。|  
  
## <a name="remarks"></a>備註  
 `IDebugPendingBreakpoint2` 可以被視為中斷點繫結至可套用至一個或多個程式的程式碼所需的所有必要資訊的提供者。  
  
 暫止中斷點可能會產生一個以上的繫結的中斷點。 例如，c + + 樣式範本中的中斷點可能會產生每個唯一的執行個體，該範本的繫結的中斷點。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)