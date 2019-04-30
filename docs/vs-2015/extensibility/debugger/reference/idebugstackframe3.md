---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 43c5b3b9bbc5e09b41f346949c4ec788c3784786
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438156"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會擴充[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)處理攔截的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 實作的相同物件上實作這個介面[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面，以支援攔截的例外狀況。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugStackFrame2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)，`IDebugStackFrame3`會公開下列方法。  
  
|方法|描述|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|處理目前的堆疊框架之前任何規則的例外狀況處理, 的例外狀況。|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|發生堆疊回溯時，會傳回程式碼內容。|  
  
## <a name="remarks"></a>備註  
 攔截到例外狀況表示偵錯工具在執行階段所呼叫任何一般的例外狀況處理常式之前，可以處理例外狀況。 攔截例外狀況，基本上指的將假裝是例外狀況處理常式存在，即使沒有執行的階段。  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)所有一般的例外狀況的回呼事件期間會呼叫 (唯一的例外是如果您正在偵錯混合模式的程式碼 （managed 和 unmanaged 程式碼），在此情況下期間無法攔截的例外狀況最後的機會獲得回呼）。 如果未實作 DE `IDebugStackFrame3`，或 DE 從 IDebugStackFrame3 傳回錯誤::`InterceptCurrentException` (這類`E_NOTIMPL`)，則偵錯工具正常處理例外狀況。  
  
 攔截例外狀況，偵錯工具可以允許使用者變更正在進行偵錯程式的狀態，然後繼續執行擲回的例外狀況之處。  
  
> [!NOTE]
> 攔截的例外狀況允許只在 managed 程式碼，也就是在 Common Language Runtime (CLR) 中執行的程式中。  
  
 偵錯引擎表示其支援攔截的例外狀況，方法是設定 「 metricExceptions"設為 1 的值在執行階段使用`SetMetric`函式。 如需詳細資訊，請參閱 <<c0> [ 進行偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [適用於偵錯的 SDK 協助程式](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
