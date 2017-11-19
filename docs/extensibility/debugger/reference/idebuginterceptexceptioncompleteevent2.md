---
title: "IDebugInterceptExceptionCompleteEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords: IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 588730d8e30044c5d5b00297a641beb9e45b17c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
這個介面是由傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) DE 攔截事件的處理完成時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來攔截的例外狀況的處理已完成的報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 DE 建立，並將此事件的物件來報告完成時攔截例外狀況的傳送。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)它附加到正在偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 `IDebugInterceptExceptionCompleteEvent2`介面會實作下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|傳回已處理的例外狀況相關聯的唯一值。|  
  
## <a name="remarks"></a>備註  
 此事件會透過傳送[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)當該方法成功完成時處理攔截例外狀況。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)