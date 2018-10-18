---
title: IDebugPort2 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 29b16652cdbed4f6e4ee2ab6b98e52ee3a868c48
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47858232"
---
# <a name="idebugport2"></a>IDebugPort2
這個介面表示在電腦上的偵錯連接埠。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者會實作這個介面來代表電腦上的偵錯連接埠。  
  
 如果連接埠支援事件的傳送埠，它也必須實作<xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>介面，以支援<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>介面，進而提供[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 若要呼叫[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)或是[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)傳回此介面，表示要求的通訊埠。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPort2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|傳回的連接埠名稱。|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|傳回的連接埠識別碼。|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|傳回用來建立連接埠 （如果有的話） 的要求。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|傳回此連接埠的連接埠供應商。|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|傳回指定處理程序的識別項的處理序的介面。|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|列舉連接埠上執行的所有處理程序。|  
  
## <a name="remarks"></a>備註  
 本機連接埠可存取所有的處理程序和本機電腦上執行的程式。 Windows CE 架構裝置的序列纜線連接或非 DCOM 電腦的網路連線，可能代表其他連接埠。 `IDebugPort2`介面用來尋找名稱和識別碼的連接埠，並列舉所有的連接埠上執行的處理程序。 啟動和終止的連接埠上的處理序的功能會實作`IDebugPortEx2`介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)