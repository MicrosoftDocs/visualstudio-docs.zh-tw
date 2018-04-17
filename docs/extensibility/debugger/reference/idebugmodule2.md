---
title: IDebugModule2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
此介面代表一個模組，也就是可執行單位程式 — 例如 DLL。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作此介面代表一個模組，並提供該模組的相關資訊的存取權。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)傳回此介面。 DE 傳送[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)介面，可以使用工作階段偵錯管理員 (SDM)[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 此介面也會傳回在[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構 (透過呼叫傳回[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md))。  
  
 [下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)也會傳回此介面 ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)傳回[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)介面)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugModule2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)描述此模組。|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已過時。 請勿使用。 重新載入此模組的符號。|  
  
## <a name="remarks"></a>備註  
 模組資訊可以顯示在**模組**在 IDE 的視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)