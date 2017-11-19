---
title: "IDebugProgramDestroyEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramDestroyEvent2
helpviewer_keywords: IDebugProgramDestroyEvent2
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: afd94114f7101f9bc2308fc233808cec5bb28f0a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyevent2"></a>IDebugProgramDestroyEvent2
這個介面是由傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 當程式執行完成。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 或自訂連接埠供應商實作這個介面可回報程式已終止，而且已無法再使用偵錯。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 或自訂連接埠供應商建立並傳送報告程式終止此事件物件。 DE 使用來傳送此事件[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。 此事件使用自訂連接埠供應商將傳送[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProgramDestroyEvent2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|取得程式的結束代碼。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)