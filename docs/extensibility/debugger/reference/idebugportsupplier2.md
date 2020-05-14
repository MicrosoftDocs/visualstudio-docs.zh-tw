---
title: IDebugPort供應商2 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724481"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
此介面向工作階段調試管理員 (SDM) 提供連接埠。

## <a name="syntax"></a>語法

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
自定義埠供應商實現此介面以表示埠供應商。

## <a name="notes-for-callers"></a>通話備註
`CoCreateInstance`使用埠供應商的`GUID`調用返回此介面(這是獲取此介面的典型方法)。 例如：

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

對[GetPortSupplier 的](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)調用返回此介面,表示[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]正在使用的 當前埠供應商。

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)返回此介面,表示創建埠的埠供應商。

- [IEnum DebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)`IDebugPortSupplier`表示`IEnumDebugPortSuppliers`介面清單( 介面是從[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]獲取的,表示註冊的所有埠供應商)。

調試引擎通常不與埠供應商互動。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
下表顯示的方法`IDebugPortSupplier2`。

|方法|描述|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|獲取埠供應商名稱。|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|獲取埠供應商識別碼。|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|從埠供應商獲取埠。|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|枚舉已存在的埠。|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|驗證埠供應商是否支援添加新埠。|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|添加埠。|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|刪除埠。|

## <a name="remarks"></a>備註
埠供應商可以按名稱和 ID 識別自身,添加和刪除埠,並枚舉埠供應商提供的所有埠。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
