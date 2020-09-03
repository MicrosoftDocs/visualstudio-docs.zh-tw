---
title: IDebugBoundBreakpoint2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad36363ff20e285dde2db6fc723ddf2562c491f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156167"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面代表系結至程式碼位置的中斷點。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 在它支援中斷點的過程中，執行這個介面。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 系結的呼叫 [會建立這個](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) 介面。 呼叫 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) 和 [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) 也可以取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugBoundBreakpoint2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|取得建立指定系結中斷點的暫止中斷點。|  
|[>getstate](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|取得這個系結中斷點的狀態。|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|取得這個系結中斷點的目前計數。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|取得描述此中斷點的中斷點解析度。|  
|[啟用](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|啟用或停用中斷點。|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|設定這個系結中斷點的計數。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設定或變更與此系結中斷點相關聯的條件。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|設定或變更與此系結中斷點相關聯的傳遞計數。|  
|[刪除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|刪除中斷點。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [下](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [綁定](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
