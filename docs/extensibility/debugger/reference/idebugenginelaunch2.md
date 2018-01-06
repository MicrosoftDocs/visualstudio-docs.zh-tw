---
title: "IDebugEngineLaunch2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineLaunch2
helpviewer_keywords: IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb53f64b6b98ed6d02774977138cfd4faf5b8f83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
使用偵錯引擎 (DE) 來啟動和終止程式。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 如果有啟動自訂連接埠無法完全處理程序的特殊需求，自訂 DE 被實作這個介面。 這通常是當 DE 是解譯器的一部分，但程序進行偵錯指令碼： 解譯器必須先啟動，然後指令碼就會載入並啟動。 連接埠可以啟動直譯器，但是指令碼可能需要特殊處理 （這是 DE 其中有一個角色）。 只有在啟動程式自訂連接埠無法處理的獨特需求，會實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面由呼叫工作階段的偵錯管理員 (SDM) 如果 SDM 可以取得此介面從[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)介面 （使用 QueryInterface）。 如果可以取得此介面，SDM 知道 DE 有特殊需求，並呼叫這個介面來啟動程式，而不需要啟動它的連接埠。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugEngineLaunch2`。  
  
|方法|描述|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|透過 DE 啟動的處理序。|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|繼續處理執行。|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|決定是否可以終止處理程序。|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|終止處理序。|  
  
## <a name="requirements"></a>需求  
 標頭： Msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)