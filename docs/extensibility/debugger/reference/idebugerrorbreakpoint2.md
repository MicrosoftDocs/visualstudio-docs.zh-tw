---
title: "IDebugErrorBreakpoint2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorBreakpoint2
helpviewer_keywords: IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b37d8596a6bf4465d1146651673acbccdd441a13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
此介面代表錯誤或警告中斷點，例如無效的位置、 運算式無效或為何暫止中斷點具有未繫結 （程式碼不會載入尚未等等） 的原因。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugErrorBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎會實作這個介面做為其支援中斷點的一部分。 這個介面用來報告問題的中斷點繫結。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)取得此介面。 此介面也會傳回 (由清單的一部分[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)介面) 的呼叫所[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)或[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugErrorBreakpoint2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|取得造成錯誤的暫止中斷點。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|取得描述錯誤的中斷點錯誤解決方式。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)