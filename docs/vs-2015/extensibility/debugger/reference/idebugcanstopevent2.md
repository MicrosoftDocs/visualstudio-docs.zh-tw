---
title: IDebugCanStopEvent2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696675"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面是用來要求會話 debug manager (SDM) 是否要在目前的程式碼位置停止。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Debug engine (DE) 會執行這個介面，以支援逐步執行原始程式碼。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須在與此介面相同的物件上執行， (SDM 使用[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)來存取 `IDebugEvent2` 介面) 。  
  
 這個介面的實作為，必須將 SDM 的 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 呼叫傳達給 debug engine。 例如，這可以透過張貼至偵測引擎訊息處理執行緒的訊息來完成，或執行此介面的物件可能會保存對偵錯工具的參考，並使用傳入的旗標回呼至偵錯工具引擎 `IDebugCanStopEvent2::CanStop` 。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 每次要求取消執行，而取消執行程式碼時，DE 可以傳送這個方法。 這個事件是在附加至所要進行的程式時，使用 SDM 提供的 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 回呼函式來傳送。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugCanStopEvent2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|取得這個事件的原因。|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|指定要進行調試的程式是否應在此事件的位置停止 (，並傳送描述停止) 或直接繼續執行之原因的事件。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|取得描述這個事件位置的檔內容。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|取得描述這個事件位置的程式碼內容。|  
  
## <a name="remarks"></a>備註  
 如果使用者逐步執行至函式，並在該處找不到任何偵測資訊，或有偵測資訊存在，而 DE 不知道是否可以顯示該位置的原始程式碼，則會傳回此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
