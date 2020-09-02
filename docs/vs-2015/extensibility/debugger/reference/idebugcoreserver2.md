---
title: IDebugCoreServer2 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c0bca6ccd3738518df339084b0f6463be181e52d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192907"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面是用來表示和取得網路上電腦上伺服器的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Visual Studio 會執行這個介面來表示伺服器。 Visual Studio 的每個實例都會建立這個介面的實例。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 自訂埠供應商會在呼叫 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)時收到這個介面。  
  
 偵錯工具引擎可以透過呼叫 ([teamfoundationserverfactory.getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) 來間接取得這個介面，此呼叫會傳回 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)，也就是衍生自) 的介面 `IDebugCoreServer2` 。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法 `IDebugCoreServer2` 。  
  
|方法|描述|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|取得電腦的名稱和屬性。|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|取得電腦的名稱。|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|取得存在於電腦上的埠供應商。|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|取得已存在於電腦上的埠。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|建立機器上所有埠的列舉值。|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|為電腦上的所有埠供應商建立枚舉器。|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|取得電腦的電腦公用程式。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 也會使用此介面來流覽在網路上的電腦上執行的處理常式。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Teamfoundationserverfactory.getserver](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
