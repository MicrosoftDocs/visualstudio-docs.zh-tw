---
title: IPropertyProxyProvider |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39cdc7769765a7680905fca5faa49222bf0a3b6d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700037"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

這個介面會提供 proxy 介面，以查看及變更物件的資料。  
  
## <a name="syntax"></a>語法  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實施者的注意事項  
 運算式評估工具 (EE) 會在實 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 介面的相同物件上，將這個介面實作為 EE 的型別視覺化支援的一部分。  
  
## <a name="notes-for-callers"></a>呼叫者注意事項  
 呼叫介面上的 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProperty3` 來取得這個介面。  
  
## <a name="methods-in-vtable-order"></a>採用 Vtable 順序的方法  
 `IPropertyProxyProvider`介面會執行下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|抓取屬性 proxy 介面，以在物件上查看資料。|  
  
## <a name="remarks"></a>備註  
 雖然 EE 會實作為這個介面，但 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) 的執行通常是由 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)處理。 如需取得 IEEVisualizerService 介面的詳細資訊，請參閱 [視覺化和查看資料](../../../extensibility/debugger/visualizing-and-viewing-data.md) 。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg。h  
  
 命名空間： VisualStudio  
  
 元件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [型別視覺化器和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [視覺化及檢視資料](../../../extensibility/debugger/visualizing-and-viewing-data.md)
