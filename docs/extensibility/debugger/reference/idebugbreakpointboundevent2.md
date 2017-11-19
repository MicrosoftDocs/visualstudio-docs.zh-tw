---
title: "IDebugBreakpointBoundEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointBoundEvent2
helpviewer_keywords: IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fe085a936c6966e42493b9f4f74dcc19ba490279
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
這個介面會告知工作階段的偵錯管理員 (SDM) 的暫止中斷點已成功繫結至載入的程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面做為其支援中斷點的一部分。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立裝置和暫止中斷點已成功繫結至偵錯程式時所傳送此事件的物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBreakpointBoundEvent2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|取得與所繫結的暫止中斷點。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|建立此事件繫結中斷點的列舉值。|  
  
## <a name="remarks"></a>備註  
 每當中斷點繫結時，就會傳送事件到 SDM。 如果中斷點無法繫結， [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)傳送，否則`IDebugBreakpointBoundEvent2`傳送。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)