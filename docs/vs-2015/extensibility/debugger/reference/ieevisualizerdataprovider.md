---
title: IEEVisualizerDataProvider |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider
helpviewer_keywords:
- IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db685850553990d6492d8da3f603e010ec0a0929
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238364"
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會提供變更物件的值，透過類型視覺化檢視的能力。  
  
## <a name="syntax"></a>語法  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來修改資料屬性在物件上支援透過類型視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面用來建立[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)物件，可透過呼叫[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)。 請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需詳細資訊。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|判斷是否可以更新物件 （且接下來，其值），代表這個視覺化檢視。|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|這個視覺化檢視的強制重新評估的物件。|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|取得這個視覺化檢視 （沒有評估完成後） 的現有物件。|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|這個視覺化檢視，藉此變更視覺化檢視提供的值會更新物件。|  
  
## <a name="remarks"></a>備註  
 視覺化檢視服務 (表示的[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)介面，並傳回[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) 會保留物件，實作的參考`IEEVisualizerDataProvider`介面. 如此一來，`IEEVisualizerDataProvider`不會實作介面實作的相同物件上[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)如果該物件會維護參考`IEEVisualizerService`物件： 循環參考結果，當物件終結時，就會發生死結。 建議的方法是實作`IEEVisualizerDataProvider`要為個別物件上`IDebugProperty2`物件而不呼叫委派`IUnknown::AddRef`在其上。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)

