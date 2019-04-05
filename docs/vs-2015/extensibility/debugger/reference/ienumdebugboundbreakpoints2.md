---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af8965e2f553f21b2e66e00189dd2fde735d1ab8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58930014"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面列舉暫止中斷點相關聯的繫結的中斷點或中斷點繫結的事件。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugBoundBreakpoints2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面做為其支援中斷點的一部分。 如果支援中斷點，則必須實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 Visual Studio 會呼叫：  
  
-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)來取得這個介面，表示所觸發的所有中斷點的清單。  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)來取得這個介面，表示已繫結的所有中斷點的清單。  
  
-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)來取得這個介面，表示所有中斷點繫結至該暫止中斷點的清單。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugBoundBreakpoints2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|擷取指定的數目的列舉型別序列中的繫結中斷點。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|略過指定的數目的列舉順序中的繫結中斷點。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|將列舉型別序列重設到開頭。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|建立列舉值，包含目前的列舉值相同的列舉型別狀態。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|取得列舉值中的繫結中斷點的數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此介面所表示的繫結的中斷點，以更新顯示在 IDE 中的中斷點。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
