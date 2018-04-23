---
title: IDebugPortSupplier2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e4aa26aa37b40c0e483342e6eb93cbac15bbbfc2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
這個介面會提供工作階段的偵錯管理員 (SDM) 連接埠。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugPortSupplier2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 自訂連接埠供應商實作這個介面來代表連接埠供應商。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫`CoCreateInstance`與連接埠供應商的`GUID`傳回此介面 （這是一般的方式取得此介面）。 例如:   
  
```cpp  
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)  
{  
    IDebugPortSupplier2 *pPS = NULL;  
    if (pPortSupplierGuid != NULL) {  
        CComPtr<IDebugPortSupplier2> spPortSupplier;  
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);  
        if (spPortSupplier != NULL) {  
            pPS = spPortSupplier.Detach();  
        }  
    }  
    return (pPS);  
}  
```  
  
 呼叫[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)傳回此介面，代表目前正在使用的連接埠供應商[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]。  
  
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)傳回此介面，代表建立連接埠的連接埠供應商。  
  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)代表清單`IDebugPortSupplier`介面 (`IEnumDebugPortSuppliers`介面取自[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)，代表所有連接埠供應商向[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).  
  
 偵錯引擎通常不會互動與連接埠供應商。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugPortSupplier2`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|取得連接埠供應商名稱。|  
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|取得連接埠供應商識別碼。|  
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|從連接埠供應商取得連接埠。|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|列舉已存在的連接埠。|  
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|確認連接埠提供者支援新增新的連接埠。|  
|[下列](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|新增連接埠。|  
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|移除連接埠。|  
  
## <a name="remarks"></a>備註  
 連接埠供應商可以識別本身的名稱和識別碼、 新增和移除連接埠，並列舉所有的連接埠供應商提供的連接埠。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)   
 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)