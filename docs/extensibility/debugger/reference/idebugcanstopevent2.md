---
title: "IDebugCanStopEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2
helpviewer_keywords: IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 585e1c8760152c9c42e1950c45d3e3821bbe93df
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
這個介面用來要求工作階段的偵錯管理員 (SDM) 是否要停止在目前的程式碼位置。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面可支援逐步執行原始程式碼。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件上 (SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面)。  
  
 這個介面的實作必須與其進行通訊的 SDM 呼叫[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)偵錯引擎。 例如，作法是使用訊息張貼至偵錯引擎的訊息處理執行緒或實作這個介面的物件可以保存的偵錯引擎的參考，旗標傳遞至回撥到偵錯引擎`IDebugCanStopEvent2::CanStop`。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 可以傳送這個方法會要求繼續執行，以 DE DE 每次會逐步執行程式碼。 此事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugCanStopEvent2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|取得這個事件的原因。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定程式偵錯時，應該停止這個事件 （與傳送事件描述停止的原因） 的位置或只繼續執行。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|取得描述這個事件的位置的文件內容。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|取得描述這個事件的位置的程式碼內容。|  
  
## <a name="remarks"></a>備註  
 如果使用者會逐步執行函式，以 DE 尋找那里無偵錯資訊，或是偵錯資訊存在但是 DE 不知道如果可以顯示該位置的原始程式碼，DE 傳送這個介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)