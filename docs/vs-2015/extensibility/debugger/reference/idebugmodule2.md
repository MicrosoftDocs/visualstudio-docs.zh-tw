---
title: IDebugModule2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fc229a353655aeae06460c32b5233888f22dd6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555804"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表模組 — 也就是程式的可執行單位，例如的 DLL。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 會實作這個介面來代表一個模組，並且可存取該模組的相關資訊。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)傳回此介面。 DE 傳送[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)介面，可以使用工作階段偵錯管理員 (SDM)[事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)方法。  
  
 此介面也會傳回在[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構 (藉由呼叫傳回哪個[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md))。  
  
 [下一步](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)也會傳回這個介面 ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)會傳回[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)介面)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugModule2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|取得[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) ，描述此模組。|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|已過時。 請勿使用。 重新載入此模組的符號。|  
  
## <a name="remarks"></a>備註  
 模組資訊可以顯示在**模組**在 IDE 的視窗。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
