---
description: 這個介面會提供方法，以在相關聯的物件上查看資料。
title: IPropertyProxyEESide |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80a295ad68341cfa4675d36b22d5de042078a0a3
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222604"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
這個介面會提供方法，以在相關聯的物件上查看資料。 此介面是類型視覺化程式支援的一部分。

## <a name="syntax"></a>Syntax

```
IPropertyProxyEESide : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會將此介面實作為支援型別視覺化程式。

## <a name="notes-for-callers"></a>呼叫者注意事項
 呼叫 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 以取得這個介面。 呼叫[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面上的[QueryInterface](/cpp/atl/queryinterface)來取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法
 下列方法是由這個介面所執行：

|方法|描述|
|------------|-----------------|
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|初始化資料來源提供者，以便存取物件的資料。|
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|抓取物件元件的相關資訊。|
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|取得物件的初始資料。|
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|建立現有資料存放區的複本。|
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|建立現有資料儲存體的參考。|
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|在包含這個物件的元件內容中，抓取特定元件的相關資訊。|

## <a name="remarks"></a>備註
 型別視覺化程式會使用此介面來存取與此介面所屬物件相關聯的值。 資料是透過 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 介面存取，它會提供資料的唯讀觀點。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
