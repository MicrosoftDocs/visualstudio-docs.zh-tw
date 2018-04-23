---
title: IEEVisualizerServiceProvider |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEVisualizerServiceProvider
helpviewer_keywords:
- IEEVisualizerServiceProvider interface
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 564251aa26bf21157e4f3792095190ede23703c8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ieevisualizerserviceprovider"></a>IEEVisualizerServiceProvider
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面可讓存取的方法，可以建立視覺化檢視服務，用來處理 IDE 類型視覺化檢視的工作。  
  
## <a name="syntax"></a>語法  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 會實作這個介面可建立視覺化檢視服務物件，接著用來提供類別 Id (`CLSID`s) 的 Visual Studio ide 的類型視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 運算式評估工具 (EE) 呼叫[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|建立視覺化檢視服務|  
  
## <a name="remarks"></a>備註  
 `IEEVisualizerServiceProvider`介面在實作期間取得[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)。 這個介面會建立視覺化檢視服務用來提供的功能[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面 EE 即負責實作。 EE 也會負責實作[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)介面，可讓類型視覺化檢視來檢視和修改屬性的值。  
  
 請參閱[Visualizing 和檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如這些介面的互動方式的詳細資訊。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)