---
title: IPropertyProxyProvider |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d6600fd9038d01c8417818886d093b5955217d03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497893"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

本主題的最新的版本可從[IPropertyProxyProvider](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyprovider)。  
  
這個介面會提供 proxy 介面來檢視及變更物件的資料。  
  
## <a name="syntax"></a>語法  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具 (EE) 實作的相同物件上實作這個介面[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) EE 支援的類型視覺化檢視的介面。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上`IDebugProperty3`介面，以取得此介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 `IPropertyProxyProvider`介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|擷取屬性 proxy 介面若要檢視的物件。|  
  
## <a name="remarks"></a>備註  
 雖然 EE 實作這個介面，實作[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)通常由[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)。 請參閱[視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)如需有關取得 IEEVisualizerService 介面。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)

