---
title: IProperty代理Eeside |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c89cecbf22091a45e31c307c5b523ac8aa4c924e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714851"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
此介面提供查看關聯對象上的數據的方法。 此介面是類型可視化器支援的一部分。

## <a name="syntax"></a>語法

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器實現此介面以支援類型可視化器。

## <a name="notes-for-callers"></a>通話備註
 調用[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)以獲取此介面。 在[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面上調使用[查詢介面](/cpp/atl/queryinterface)以取得[IPropertyProxy 提供程式介面](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 以下方法由此介面實現:

|方法|描述|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|初始化資料來源提供者,以便可以存取物件資料。|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|檢索有關物件程序集的資訊。|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|獲取對象的初始數據。|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|建立現有資料存儲的複本。|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|創建對現有資料存儲的引用。|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|檢索包含此物件的程式集上下文中的特定程式集的資訊。|

## <a name="remarks"></a>備註
 類型可視化工具使用此介面訪問與此介面所參與的物件關聯的值。 數據通過[IEEDataStorage介面](../../../extensibility/debugger/reference/ieedatastorage.md)進行訪問,該介面提供數據的唯讀檢視。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
