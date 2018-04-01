---
title: IEnumDebugPortSuppliers2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugPortSuppliers2
helpviewer_keywords:
- IEnumDebugPortSuppliers2
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1fff85e5cb76293327138bf6382c8e0f4da06c25
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugportsuppliers2"></a>IEnumDebugPortSuppliers2
這個介面會列舉連接埠供應商。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 實作此介面代表連接埠供應商的清單。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)以取得連接埠供應商的清單。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugPortSuppliers2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|擷取指定的數目的列舉順序中的連接埠供應商。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|略過指定的數目的列舉順序中的連接埠供應商。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|取得列舉值中的連接埠供應商的數目。|  
  
## <a name="remarks"></a>備註  
 偵錯引擎通常不需要以取得此介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)