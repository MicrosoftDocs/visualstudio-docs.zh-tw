---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ece720cf6880bba528dee99cdbdeb25c10087a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674136"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

此介面可讓呼叫端判斷連接埠提供者是否可以保留連接埠 （寫入磁碟） 的偵錯工具的引動過程之間，然後以取得這些保留的連接埠清單。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 自訂的連接埠提供者會實作此介面支援保存或儲存至磁碟的連接埠資訊。 必須為相同的物件上實作這個介面[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugPortSupplier2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自方法[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面，此介面支援下列：  
  
|方法|描述|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|傳回是否連接埠提供者可以保存連接埠 （藉由將它們寫入磁碟） 的偵錯工具的引動過程之間。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|傳回可用來列舉透過所有連接埠已寫入磁碟的這個連接埠提供者的物件。|  
  
## <a name="remarks"></a>備註  
 如果連接埠提供者可以跨引動過程中保存連接埠，它應該實作這個介面。 當連接埠提供者具現化，而且連接埠提供者被終結時寫入磁碟時，應該載入的連接埠。  
  
 偵錯引擎通常不會使用連接埠提供者互動，而且必須沒有使用此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
