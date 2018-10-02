---
title: IDebugCoreServer3 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1c039ccb08f7143112939f9d7880d508bd079a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500619"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugCoreServer3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver3)。  
  
此介面可讓的伺服器處理序正在執行中的相關資訊的存取。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 Visual Studio 會實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)若要取得從這個介面[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面。 呼叫[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)也可以傳回此介面。 這個介面是最常使用之自訂的連接埠提供者來啟動伺服器 （本機或遠端） 上的程式。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|擷取伺服器的名稱。|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|擷取伺服器名稱的易記版本|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|會告知的處理序啟動時，會自動附加至處理序特定的偵錯引擎。|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|會自動附加動作失敗時，請擷取特定的錯誤碼。|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|在伺服器上建立偵錯引擎執行的個體。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|擷取旗標，指出伺服器是否與呼叫端相同的電腦上。|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|擷取值，指出用來與伺服器通訊的通訊協定。|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|停用所有自動都附加此伺服器所知道的所有偵錯引擎設定。|  
  
## <a name="remarks"></a>備註  
 自訂連接埠供應商收到[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)介面上呼叫[事件](../../../extensibility/debugger/reference/idebugportevents2-event.md)。 `IDebugCoreServer3`介面可以取自該介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)

