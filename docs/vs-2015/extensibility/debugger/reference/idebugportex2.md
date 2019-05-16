---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb866c5cb968a4f03c718f04193026ac5308f7d4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65681127"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面可讓偵錯管理員 (SDM) 控制項，程式和連接埠上執行的處理序的工作階段。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者所實作的相同物件上實作這個介面[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 SDM 呼叫[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugPort2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortEx2`。  
  
|方法|描述|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|會啟動可執行檔。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|繼續執行的處理序。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|判斷是否可以終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|結束處理序。|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|取得本身的連接埠的處理序識別碼。|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|取得與程式節點相關聯的程式。|  
  
## <a name="remarks"></a>備註  
 這個介面是 SDM 和自訂的連接埠提供者之間通常私用。  
  
 如有需要，此介面可以尋找偵錯引擎 (DE) [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面傳遞給[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)並用[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)啟動程式。 這不是必要需求，但 DE 可以執行任何手動啟動要求的程式。  
  
## <a name="requirements"></a>需求  
 標頭： portpriv.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
