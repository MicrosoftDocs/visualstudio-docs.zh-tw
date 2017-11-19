---
title: "IDebugBreakpointRequest3 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointRequest3
helpviewer_keywords: IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f96bbb9e06b81e648df3d9cd3812d0871c149cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
此介面代表建立並繫結任何中斷點類型的所需的資訊。 它是一個擴充的[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 工作階段的偵錯管理員 (SDM) 通常會實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 偵錯引擎 (DE) 存取這個介面，藉由呼叫[QueryInterface](/cpp/atl/queryinterface) IDebugBreakpointRequest2 介面的呼叫中收到[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)、`IDebugBreakpointRequest3`介面會公開下列方法。  
  
|方法|說明|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|取得描述此中斷點要求的中斷點要求資訊。|  
  
## <a name="remarks"></a>備註  
 這個介面用來提供其他資訊給透過 DE [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構。 這項額外資訊包括 DE 廠商識別碼 （中的 GUID 格式）、 追蹤點的名稱和中斷點條件約束的名稱。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)