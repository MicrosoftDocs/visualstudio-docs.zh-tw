---
title: IProperty代理供應商 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f71d993c7f99cade5b866e67298132a325986e3a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714786"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
此介面提供代理介面來查看和更改物件的數據。

## <a name="syntax"></a>語法

```
IPropertyProxyProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器 (EE) 在實現[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面的同一物件上實現此介面,作為 EE 支援類型可視化器的一部分。

## <a name="notes-for-callers"></a>通話備註
 在`IDebugProperty3`介面上調用[查詢介面](/cpp/atl/queryinterface)以獲取此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 介面`IPropertyProxyProvider`實作以下方法:

|方法|描述|
|------------|-----------------|
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|檢索屬性代理介面以查看對象上的數據。|

## <a name="remarks"></a>備註
 儘管 EE 實現了此介面,但[GetProperty Proxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)的實現通常由[GetProperty Proxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)處理。 有關取得 IEE 視覺化服務介面的詳細資訊,請參閱[可視化和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
