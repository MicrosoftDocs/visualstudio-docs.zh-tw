---
title: IEE可視化服務提供者 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44d8a73589a4248736ac6c4d73814166056a1f90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717880"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 此介面允許訪問一個可以創建可視化工具服務的方法,該服務用於處理IDE的類型可視化器任務。

## <a name="syntax"></a>語法

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者說明
 Visual Studio 實現此介面以建立視覺化工具服務物件,而可視化物件又用於向 Visual Studio IDE`CLSID`提供類型視覺化器的類 IDE。

## <a name="notes-for-callers"></a>通話備註
 運算式賦值器 (EE) 呼叫[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)以取得此介面。

## <a name="methods-in-vtable-order"></a>依 Vtable 順序排列的方法

|方法|描述|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|建立視覺化工具服務|

## <a name="remarks"></a>備註
 該`IEEVisualizerServiceProvider`介面是在[實現評估同步](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)期間獲得的。 此介面創建的可視化工具服務用於向[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面提供功能,EE 負責實現該介面。 EE 還負責實現[IEE 可視化數據提供程式](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)介面,該介面允許類型可視化器查看和修改屬性的值。

 有關這些介面如何互動的詳細資訊,請參閱[視覺化和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)。

## <a name="requirements"></a>需求
 標題: ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
