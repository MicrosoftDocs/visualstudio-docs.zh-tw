---
title: "IDebugCoreServer2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2
helpviewer_keywords: IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31961d62c2ef7a253a16a5384dfa6b5e69209a97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
這個介面用來代表，並從網路上的電腦上的伺服器取得的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 實作此介面來代表伺服器。 Visual Studio 的每個執行個體建立這個介面的執行個體。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 自訂連接埠供應商收到此介面的呼叫中[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。  
  
 偵錯引擎可以取得間接透過呼叫這個介面[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (它會傳回[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)，衍生自介面`IDebugCoreServer2`)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugCoreServer2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|取得機器的屬性與名稱。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|取得機器的名稱。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|取得連接埠供應商存在於電腦上。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|取得已經存在電腦的連接埠。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|在電腦上建立的所有連接埠的列舉值。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|在電腦上建立所有連接埠供應商的列舉的值。|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|取得機器的機器公用程式。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 也會使用此介面來瀏覽網路上的電腦上執行的處理程序。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)