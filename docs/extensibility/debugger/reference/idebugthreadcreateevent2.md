---
title: "IDebugThreadCreateEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThreadCreateEvent2
helpviewer_keywords: IDebugThreadCreateEvent2
ms.assetid: aee34a14-4f9c-4ad3-845f-c96ee938cefd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa5919b10df6c11089d5d8bd719a240ad2c54ceb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthreadcreateevent2"></a>IDebugThreadCreateEvent2
這個介面是由傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 時進行偵錯程式中會建立一個執行緒。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugThreadCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來回報已經建立的執行緒。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 會建立並傳送報告執行緒已建立此事件物件。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至正在進行偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)