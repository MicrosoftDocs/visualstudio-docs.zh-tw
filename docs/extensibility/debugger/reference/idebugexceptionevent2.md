---
title: IDebugExceptionEvent2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: dc6dacbac1092e211ba129417bd4e47aea31b733
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
偵錯引擎 (DE) 目前正在執行的程式中擲回例外狀況時，將此介面傳送至工作階段的偵錯管理員 (SDM)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExceptionEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來進行偵錯的程式中發生了例外的報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和傳送此事件物件，來報告例外狀況。 事件使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugExceptionEvent2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|取得有關引發這個事件的例外狀況的詳細的資訊。|  
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|取得引發這個事件的例外狀況擲回的人們可讀取描述。|  
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|決定偵錯引擎 (DE) 支援將此例外狀況傳遞至偵錯時就會繼續執行程式的選項。|  
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|指定例外狀況應該傳遞給程式進行偵錯時就會繼續執行，或如果應該捨棄例外狀況。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>備註  
 在之前傳送事件，DE 檢查是否這個例外狀況事件已指定發生第一個或第二個可能的例外狀況由先前呼叫[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)。 如果已指定為第一個可能發生的例外狀況，`IDebugExceptionEvent2`會傳送事件至 SDM。 如果沒有，DE 可讓應用程式有機會處理此例外狀況。 如果已不提供任何例外狀況處理常式，而且例外狀況已指定為第二個可能的例外狀況，`IDebugExceptionEvent2`會傳送事件至 SDM。 否則 DE 會繼續執行程式，而且作業系統或執行階段處理的例外狀況。  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)