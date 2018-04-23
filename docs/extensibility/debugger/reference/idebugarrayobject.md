---
title: IDebugArrayObject |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cac7730296d2a4f95563c3d6ff4c60fdd294dc6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 此介面代表陣列物件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具會實作這個介面來表示陣列。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面可以取得此介面使用[QueryInterface](/cpp/atl/queryinterface)如果所代表的物件陣列。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 除了上`IDebugObject`介面上實作下列方法`IDebugArrayObject`介面。  
  
|方法|描述|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|陣列中取得的項目計數。|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|取得陣列的項目。|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|取得陣列的所有項目。|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|取得陣列的陣序規範。|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|取得陣列維度。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用此介面來代表剖析樹狀目錄中的陣列。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)