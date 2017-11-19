---
title: "IDebugPropertyDestroyEvent2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPropertyDestroyEvent2
helpviewer_keywords: IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5035ffcbe67b13306652c6de079506866d7251a3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
這個介面是由傳送偵錯引擎 (DE) 工作階段的偵錯管理員 (SDM) 與特定文件相關聯的屬性即將終結時。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 DE 實作這個介面可報告屬性已被終結。 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)介面必須實作此介面為相同的物件。 SDM 使用[QueryInterface](/cpp/atl/queryinterface)存取`IDebugEvent2`介面。 如果 DE 先前已建立的指令碼; 相關聯的屬性，會實作這個介面終結屬性從 IDE 中移除相關聯的指令碼。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 建立和此事件會將物件傳送至報表的屬性已被終結。 事件會使用傳送[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)附加至正在進行偵錯程式時，會將 SDM 所提供的回呼函式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPropertyDestroyEvent2`。  
  
|方法|說明|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|取得屬性，也將被銷毀。|  
  
## <a name="remarks"></a>備註  
 請參閱備註[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)並使用這些事件的詳細資料的原因。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)