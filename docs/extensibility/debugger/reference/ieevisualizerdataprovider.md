---
description: 這個介面可讓您透過型別視覺化程式來變更物件的值。
title: IEEVisualizerDataProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6af1f32a627b713c7907c9de29470f7624fdd7e4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080290"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面可讓您透過型別視覺化程式來變更物件的值。

## <a name="syntax"></a>Syntax

```
IEEVisualizerDataProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 運算式評估工具會執行這個介面，以支援透過型別視覺化來修改屬性物件上的資料。

## <a name="notes-for-callers"></a>呼叫者注意事項
 這個介面是用來透過呼叫[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)來建立[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)物件。 如需詳細資料，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法

|方法|描述|
|------------|-----------------|
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|判斷是否可以更新物件 (以及之後的值) 這個視覺化程式所代表的值。|
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|強制重新評估這個視覺化檢視的物件。|
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|取得此視覺化檢視的現有物件 (不會) 完成評估。|
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|更新此視覺化程式的物件，藉此變更視覺化程式所呈現的值。|

## <a name="remarks"></a>備註
 視覺化程式服務 (以 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 介面表示，並由 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 所傳回) 保留對執行介面之物件的參考 `IEEVisualizerDataProvider` 。 如此一來， `IEEVisualizerDataProvider` 如果物件會維護物件的參考，則不應在執行 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 的相同物件上實介面 `IEEVisualizerService` ：迴圈參考結果，以及當物件終結時，就會發生鎖死。 建議的方法是 `IEEVisualizerDataProvider` 在物件委派的另一個物件上執行， `IDebugProperty2` 而不需要 `IUnknown::AddRef` 對其進行呼叫。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
