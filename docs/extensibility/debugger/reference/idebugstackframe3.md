---
title: "IDebugStackFrame3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame3
helpviewer_keywords: IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ed100cce9e4677538f12973b6c5586dce0d0548
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
這個介面延伸[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)處理攔截的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 實作的相同物件上實作此介面[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面，以支援攔截的例外狀況。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugStackFrame2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)，`IDebugStackFrame3`會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|處理目前的堆疊框架之前的任何規則的例外狀況處理, 的例外狀況。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|如果會發生堆疊回溯，則傳回程式碼內容。|  
  
## <a name="remarks"></a>備註  
 攔截例外狀況表示偵錯工具在任何標準的例外狀況處理常式會呼叫執行階段之前，可以處理例外狀況。 基本上，攔截例外狀況，表示將假裝例外狀況處理常式存在，即使沒有在執行的階段。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)所有一般的例外狀況回呼事件期間會呼叫 (唯一的例外是如果您正在偵錯混合模式程式碼 （managed 與 unmanaged 程式碼），在此情況下無法攔截的例外狀況時最後一個機會回呼）。 如果未實作 DE `IDebugStackFrame3`，或 DE 從 IDebugStackFrame3 傳回錯誤::`InterceptCurrentException` (例如`E_NOTIMPL`)，然後偵錯工具正常處理例外狀況。  
  
 偵錯工具可以攔截例外狀況，允許使用者變更正在進行偵錯程式的狀態，然後繼續執行擲回例外狀況所在的點。  
  
> [!NOTE]
>  攔截的例外狀況允許只在 managed 程式碼，也就是在程式中執行 Common Language Runtime (CLR) 下。  
  
 偵錯引擎指示它支援攔截的例外狀況藉由設定 「 metricExceptions"設為 1 的值在執行階段使用`SetMetric`函式。 如需詳細資訊，請參閱[SDK 進行偵錯的協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)