---
title: "IDebugThread2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2
helpviewer_keywords: IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0acb0a0785f7cb493df30af8d828cf64b5372cae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2"></a>IDebugThread2
此介面代表在程式中執行的執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugThread2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表單一程式中執行的執行緒。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)取得此介面，代表目前作用中的執行緒。  
  
 此介面也會用於建立中斷點要求 (請參閱[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md))。  
  
 此介面也會傳回解析繫結或錯誤的中斷點時 (請參閱[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)和[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md))。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugThread2`。  
  
|方法|說明|  
|------------|-----------------|  
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|擷取這個執行緒的堆疊框架的清單。|  
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|取得執行緒的名稱。|  
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|設定執行緒的名稱。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|取得執行緒正在執行的程式。|  
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|判斷下一個陳述式是否可以設定特定的堆疊框架和程式碼內容。|  
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|將下一個陳述式設定為特定的堆疊框架和程式碼內容。|  
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|取得系統執行緒識別碼。|  
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|暫止的執行緒。|  
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|繼續執行緒。|  
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|取得描述執行緒屬性。|  
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|取得與這個實體的執行緒相關聯的邏輯執行緒。|  
  
## <a name="remarks"></a>備註  
 由於在多個程式中，多個可執行的單一實體執行緒`IDebugThread2`從多個程式可以代表相同的實體執行緒。  
  
 中斷點或例外狀況發生時，就會傳送事件藉由呼叫[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)。 這個方法的引數的其中一個是`IDebugThread2`代表目前執行緒的介面。 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)用來取得[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面目前的堆疊框架。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)