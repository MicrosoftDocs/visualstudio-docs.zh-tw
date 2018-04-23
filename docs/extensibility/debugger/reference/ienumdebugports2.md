---
title: IEnumDebugPorts2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 07018391b51424b65bf1e8b9040f637f6f22213e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
這個介面會列舉電腦或通訊埠的供應商的連接埠。  
  
## <a name="syntax"></a>語法  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作這個介面來代表供應商所建立的連接埠清單。 Visual Studio 實作此介面來支援它自己的連接埠供應商。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)取得此介面代表連接埠供應商所建立的連接埠清單。 呼叫[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)取得此介面代表一份已儲存的連接埠至磁碟。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IEnumDebugPorts2`。  
  
|方法|描述|  
|------------|-----------------|  
|[下一步](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|擷取指定的數目的列舉順序中的連接埠。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|略過指定的數目的列舉順序中的連接埠。|  
|[重設](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|列舉序列重設為開頭。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|建立列舉值，包含目前的列舉值的列舉型別狀態相同。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|取得列舉值中的連接埠數目。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會使用此介面來協助填入的連接埠用於附加至處理序清單。  
  
 偵錯引擎通常不使用這個介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)