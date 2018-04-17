---
title: IPropertyProxyEESide |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 90f34e954945f6b557f8c5e1f5ac0b0802e1e663
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
這個介面會提供方法來檢視相關聯的物件上的資料。 這個介面是支援的類型視覺化檢視的一部分。  
  
## <a name="syntax"></a>語法  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 運算式評估工具會實作這個介面以支援類型的視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)取得此介面。 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下列方法會實作這個介面：  
  
|方法|描述|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|初始化資料來源提供者，以便可存取物件的資料。|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|擷取物件的組件的相關資訊。|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|取得物件的初始資料。|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|建立現有的資料儲存區的複本。|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|建立現有的資料儲存體的參考。|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|擷取包含此物件的組件的內容中的特定組件的相關資訊。|  
  
## <a name="remarks"></a>備註  
 類型的視覺化檢視會使用此介面來存取此介面是一部分的物件相關聯的值。 資料透過存取[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)介面，可提供資料的唯讀檢視。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [類型的視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)