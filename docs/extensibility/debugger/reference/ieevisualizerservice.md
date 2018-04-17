---
title: IEEVisualizerService |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 17
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 97701dede6a3e6b17911f6ab3c5e37dfdd90cc58
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會實作主要的方法可提供功能以[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)和[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。  
  
## <a name="syntax"></a>語法  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 Visual Studio 會實作這個介面可允許的運算式評估工具 (EE) 以支援類型的視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 EE 呼叫[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)類型視覺化檢視這個介面取得做為其支援的一部分。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|擷取有關哪些知道這個服務的自訂檢視器的數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|擷取自訂檢視器的清單。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|傳回屬性的 proxy 物件。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|擷取值的字串，以顯示指定的屬性或欄位的數目。|  
  
## <a name="remarks"></a>備註  
 IDE 使用[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以判斷是否有任何自訂檢視器，或輸入屬性的視覺化檢視。 藉由建立視覺化檢視服務 (與[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md))，卻可以提供的功能`IDebugProperty3`和[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (可支援檢視和變更屬性的值） 介面，並藉此支援類型的視覺化檢視。  
  
 如果 EE 自訂檢視器本身所實作，可以將附加 EE`CLSID`這些自訂檢視器所傳回的清單結尾的 s [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)。 這可讓 EE 支援類型的視覺化檢視和它自己的自訂檢視器。 就無法確定[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)反映出加入的任何自訂檢視器。  
  
 請參閱[類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)視覺化檢視和檢視器之間的差異的討論。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)