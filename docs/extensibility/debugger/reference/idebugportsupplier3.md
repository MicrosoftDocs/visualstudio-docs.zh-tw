---
title: IDebugPortSupplier3 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f0e1c5c252e0674ee3de8371080e298f42de2112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
這個介面可讓呼叫端判斷連接埠供應商可以保留連接埠 （寫入磁碟） 的偵錯工具的引動過程之間，然後取得這些保留的連接埠清單。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作此介面支援保存或儲存至磁碟的連接埠資訊。 必須為相同的物件上實作這個介面[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](/cpp/atl/queryinterface)上`IDebugPortSupplier2`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了繼承自[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)介面，此介面支援下列：  
  
|方法|描述|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|傳回是否連接埠供應商可以保存連接埠 （藉由將它們寫入至磁碟） 的偵錯工具的引動過程之間。|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|傳回可以用來列舉所有的連接埠已寫入磁碟的這個連接埠供應商所透過的物件。|  
  
## <a name="remarks"></a>備註  
 如果連接埠供應商可以跨引動過程中保存連接埠，則它應該實作這個介面。 當具現化，且寫入磁碟的連接埠供應商終結時的連接埠供應商應該載入的連接埠。  
  
 偵錯引擎通常與連接埠供應商不會互動，而不會使用這個介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)