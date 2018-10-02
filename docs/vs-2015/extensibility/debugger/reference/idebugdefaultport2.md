---
title: IDebugDefaultPort2 |Microsoft Docs
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
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d2465d5c0d9a28904751b71c29401655f3d5f18
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496732"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IDebugDefaultPort2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdefaultport2)。  
  
這個介面會提供數種方法可以存取連接埠的伺服器和通知功能。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 Visual Studio 會實作這個介面來代表存取程式的偵錯連接埠。 如果它會處理遠端偵錯自訂連接埠供應商也可以實作這個介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 方法的引數[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)介面會提供這個介面。 呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)介面也可以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 中定義的方法除了[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|從這個連接埠取得連接埠告知介面。|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|主控此連接埠的伺服器中取得的介面。|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|判斷是否要將此連接埠執行本機電腦上。|  
  
## <a name="remarks"></a>備註  
 名稱"`IDebugDefaultPort2`」 是一堆一點點，因為它不代表預設連接埠。 會將它稱為 「 IDebugPort3。 」  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

