---
title: "IDebugModuleLoadEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugModuleLoadEvent2
helpviewer_keywords: IDebugModuleLoadEvent2 interface
ms.assetid: 7d26fb23-5d49-4ba7-b7c5-3aed4d7be81e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c74ec97e127517ed800469d18b961207231466ed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmoduleloadevent2"></a>IDebugModuleLoadEvent2
這個介面是由傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 時載入或卸載模組。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModuleLoadEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面來模組已載入或卸載報表。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和此事件會將物件傳送至報表載入或卸載模組。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至正在進行偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugModuleLoadEvent2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)|取得模組，正在載入或卸載。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此事件保留**模組**視窗的最新狀態。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)