---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d7578bc8564e65211ec809710e4f69ec96bcdf5d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920352"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

使用偵錯引擎 (DE) 來啟動和終止程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 如果有啟動處理程序無法完全由自訂連接埠處理的特殊需求，自訂 DE 被實作這個介面。 這通常是 DE 屬於解譯器和正在偵錯的程序是指令碼時的案例： 解譯器必須首先，啟動，而且就會再載入指令碼並將其啟動。 連接埠可以啟動解譯器，但指令碼可能需要特殊處理 （這是其中 DE 扮演的角色）。 只有當有獨特的需求，來啟動自訂的連接埠無法處理的程式時，才會實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面由工作階段的偵錯管理員 (SDM) 如果 SDM 可以取得此介面從呼叫[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面 （使用 QueryInterface）。 如果可以取得此介面，SDM 知道 DE 有特殊需求，並呼叫這個介面來啟動程式，而不需要啟動它的連接埠。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngineLaunch2`。  
  
|方法|描述|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|透過 DE 啟動處理序。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|繼續處理序執行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|決定是否會終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|結束處理序。|  
  
## <a name="requirements"></a>需求  
 標頭：Msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
