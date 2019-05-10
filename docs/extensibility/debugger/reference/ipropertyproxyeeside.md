---
title: IPropertyProxyEESide | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8a75aa089d516f112d1c758cc161891aa26e0d2
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65461068"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
這個介面會提供方法來檢視相關聯的物件上的資料。 這個介面是支援的類型視覺化檢視的一部分。

## <a name="syntax"></a>語法

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>實作者的附註
 運算式評估工具會實作這個介面，以支援類型視覺化檢視。

## <a name="notes-for-callers"></a>呼叫端資訊
 呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)來取得這個介面。 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。

## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法
 下列方法會實作此介面：

|方法|描述|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|初始化資料來源提供者，以便您可以存取物件的資料。|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|擷取物件的組件的相關資訊。|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|取得物件的初始資料。|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|建立的現有的資料存放區的複本。|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|建立現有的資料儲存體的參考。|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|擷取包含這個物件的組件的內容中的特定組件相關資訊。|

## <a name="remarks"></a>備註
 類型視覺化檢視會使用此介面來存取這個介面是一部分的物件相關聯的值。 透過存取的資料[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面，可提供資料的唯讀檢視。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)