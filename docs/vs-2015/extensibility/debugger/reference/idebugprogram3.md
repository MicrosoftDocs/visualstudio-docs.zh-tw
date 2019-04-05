---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58944083"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面代表一個程式正在執行的處理序中，擴充[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)藉由提供執行緒資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 偵錯引擎 (DE) 和自訂的連接埠提供者實作這個介面來代表處理程序中的程式。 工作階段的偵錯管理員 (SDM) 也會實作這個介面來提供資訊給[附加](../../../extensibility/debugger/reference/idebugprogram2-attach.md)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件會傳回此新的程式的介面。 此介面也做為參數的多個介面上的許多方法。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugProgram3`。  
  
|方法|描述|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|執行程式。 執行緒會傳回給哪一個執行緒執行時，正在檢視使用者的偵錯工具資訊。|  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>備註  
 程式是處理程序組成一或多個程式時，在特定的執行階段架構中，執行的執行緒容器。  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [下一步](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [附加](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [事件](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
