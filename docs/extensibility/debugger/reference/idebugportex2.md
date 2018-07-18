---
title: IDebugPortEx2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6742b18c426c193716151e43cdd5b277c387e4c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117848"
---
# <a name="idebugportex2"></a>IDebugPortEx2
這個介面可讓偵錯管理員 (SDM) 控制項的程式和連接埠上執行的處理序的工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作此介面實作在相同物件上[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 SDM 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugPort2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortEx2`。  
  
|方法|描述|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|會啟動可執行檔。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|繼續執行的處理程序。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|決定是否可以終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|終止處理序。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|取得本身的連接埠的處理序識別碼。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|取得與程式節點相關聯的程式。|  
  
## <a name="remarks"></a>備註  
 這個介面是 SDM 與自訂連接埠供應商之間通常私用。  
  
 如有需要，偵錯引擎 (DE) 可以此介面上尋找[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面傳遞到[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)並用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)来啟動程式。 這不是必要條件，不過，並將 DE 可以執行它所要執行您要啟動要求的程式。  
  
## <a name="requirements"></a>需求  
 標頭： portpriv.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)