---
title: IEEVisualizerService |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService
helpviewer_keywords:
- IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b3bb741aa25cf6695f1dd1d8d66fc0c1846413b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838917"
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會實提供功能給 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 和 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) 介面的主要方法。  
  
## <a name="syntax"></a>語法  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 Visual Studio 會執行這個介面，以允許運算式評估工具 (EE) 支援型別視覺化程式。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 EE 會呼叫 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) 來取得此介面，作為其對視覺化類型的支援。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|抓取此服務知道的自訂檢視器數目。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|抓取自訂檢視器清單。|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|傳回屬性的 proxy 物件。|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|抓取要針對指定的屬性或欄位顯示的值字串數目。|  
  
## <a name="remarks"></a>備註  
 IDE 會使用 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 介面來判斷屬性是否有任何自訂檢視器或型別視覺化程式。 藉由建立[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) 的視覺化服務 (，EE 可以提供和 IPropertyProxyEESide (的功能，以 `IDebugProperty3` 支援) 介面查看和變更屬性的值，進而支援型別視覺化程式。 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
 如果 EE 具有自行實行的自訂檢視器，則 EE 可將 `CLSID` 這些自訂檢視器的 s 附加至 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)傳回的清單結尾。 這可讓 EE 支援型別視覺化程式和自己的自訂檢視器。 只要確定 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) 會反映出新增的任何自訂檢視器。  
  
 請參閱 [型別視覺化程式和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) ，以取得視覺化檢視和檢視器之間差異的討論。  
  
## <a name="requirements"></a>需求  
 標頭： ee. h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
