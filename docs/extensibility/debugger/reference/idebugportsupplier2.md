---
title: IDebugPortSupplier2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf9cd3cb82e2b14811a8ec52a651248e2990ae27
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840362"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
這個介面會提供埠給會話 debug manager (SDM) 。

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
自訂埠供應商會將此介面實作為代表埠供應商的介面。

## <a name="notes-for-callers"></a>呼叫者注意事項
`CoCreateInstance`使用埠供應商的呼叫會傳回 `GUID` 這個介面 (這是) 取得此介面的一般方式。 例如：

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

對 [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) 的呼叫會傳回這個介面，代表目前所使用的通訊埠供應商 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) 會傳回這個介面，代表建立埠的埠供應商。

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) 代表介面的清單 `IDebugPortSupplier` `IEnumDebugPortSuppliers` ， (可從 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)取得介面，表示所有向) 註冊的埠供應商 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。

Debug engine 通常不會與埠供應商互動。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法 `IDebugPortSupplier2` 。

|方法|描述|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|取得埠供應商名稱。|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|取得埠供應商識別碼。|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|從埠供應商取得埠。|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|列舉已存在的埠。|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|確認埠供應商支援新增埠。|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|新增埠。|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|移除埠。|

## <a name="remarks"></a>備註
埠供應商可以依名稱和識別碼來識別本身、新增和移除埠，以及列舉埠供應商所提供的所有埠。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
