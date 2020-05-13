---
title: IEEData儲存 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad7da71d31e1093d87d68bb39958a71a117f5d5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718183"
---
# <a name="ieedatastorage"></a>IEEDataStorage
此介面表示位元組。

## <a name="syntax"></a>語法

```
IEEDataStorage : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 運算式賦值器 (EE) 實現此介面以表示位元組(類型可視化器用於透過[IProperty ProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面檢索和更改數據)。 EE 通常實現此介面以支援外部類型可視化工具。

## <a name="notes-for-callers"></a>通話備註
 介面上`IPropertyProxyEESide`的方法都返回此介面。 呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)以取得[IPropertyProxyEESide 介面](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)。 在[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面上調使用[查詢介面](/cpp/atl/queryinterface)以取得[IPropertyProxy 提供程式介面](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法
 介面`IEEDataStorage`實作以下方法:

|方法|描述|
|------------|-----------------|
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|將指定的數據位元組數檢索到提供的緩衝區。|
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|檢索可用數據位元組數。|

## <a name="remarks"></a>備註
 此介面由類型可視化器用於存取特定物件持有的數據。 數據被視為位元組,允許類型可視化器以向使用者呈現數據所需的任何方式操作數據。

 如果需要,自定義查看器也可以使用此介面,儘管更通常自定義查看器將使用自定義介面[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)或[GetStringChars(](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)對於面向字串的數據)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
