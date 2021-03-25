---
description: 這個介面可讓您存取可建立視覺化程式服務的方法，此服務可用來處理 IDE 的型別視覺化工作。
title: IEEVisualizerServiceProvider |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 973135865b0b1c460f4c9000036f2af04a9ae3ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086686"
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 這個介面可讓您存取可建立視覺化程式服務的方法，此服務可用來處理 IDE 的型別視覺化工作。

## <a name="syntax"></a>Syntax

```
IEEVisualizerServiceProvider : IUnknown
```

## <a name="notes-for-implementers"></a>實施者的注意事項
 Visual Studio 會執行此介面來建立視覺化程式服務物件，該物件接著會用來將型別 `CLSID` 視覺化) 的類別 (識別碼提供給 VISUAL STUDIO IDE。

## <a name="notes-for-callers"></a>呼叫者注意事項
 運算式評估工具 (EE) 呼叫 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) 來取得這個介面。

## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法

|方法|描述|
|------------|-----------------|
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|建立視覺化服務|

## <a name="remarks"></a>備註
 `IEEVisualizerServiceProvider`介面是在[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的執行期間取得。 此介面所建立的視覺化程式服務會用來提供功能給 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 介面，而此介面會由 EE 負責執行。 此 EE 也負責實 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 介面，讓型別視覺化程式能夠查看和修改屬性的值。

 如需這些介面互動方式的詳細資訊，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。

## <a name="requirements"></a>規格需求
 標頭： ee. h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Expression Evaluation Interfaces](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
