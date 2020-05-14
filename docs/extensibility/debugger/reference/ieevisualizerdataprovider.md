---
title: IEE視覺化資料提供者 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a10f306b6c507f6db7add17931b8a38d926a37d9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718061"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面提供透過類型可視化工具更改物件值的功能。

## <a name="syntax"></a>語法

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 表達式賦值器實現此介面以支援通過類型可視化器修改屬性對象上的數據。

## <a name="notes-for-callers"></a>通話備註
 此介面用於透過呼叫[創建視覺化](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)服務創建[IEEVisualizer服務](../../../extensibility/debugger/reference/ieevisualizerservice.md)物件。 關於詳細資訊[,請參閱可視化和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法

|方法|描述|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|確定是否可以更新此可視化工具表示的物件(以及隨後的其值)。|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|強制重新評估此可視化工具的物件。|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|獲取此可視化工具的現有物件(未執行任何評估)。|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|更新此可視化工具的物件,從而更改可視化工具提供的值。|

## <a name="remarks"></a>備註
 可視化工具服務(由[IEEVisualizer 服務](../../../extensibility/debugger/reference/ieevisualizerservice.md)介面表示並由[CreateVisualizer 服務](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)返回)保留對實現`IEEVisualizerDataProvider`該介面的物件的引用。 因此,`IEEVisualizerDataProvider`如果該物件維護`IEEVisualizerService`對 物件的引用,則介面不應在實現[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)的同一對象上實現:迴圈引用結果,並在物件被銷毀時發生死鎖。 建議的方法是在物件委託給的`IEEVisualizerDataProvider`單獨物件上實現`IDebugProperty2`, 而不`IUnknown::AddRef`調用 它。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
