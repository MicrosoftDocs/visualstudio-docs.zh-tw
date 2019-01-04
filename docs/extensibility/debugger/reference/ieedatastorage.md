---
title: IEEDataStorage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0db1dc01c67c93c5cabfb40af8acf55b34ad660
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820143"
---
# <a name="ieedatastorage"></a>IEEDataStorage
這個介面會表示為位元組陣列。  
  
## <a name="syntax"></a>語法  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具 (EE) 會實作這個介面來表示的位元組陣列 (用來擷取和變更資料類型視覺化檢視[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面)。 EE 通常會實作這個介面來支援外部類型視覺化檢視。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 上的方法`IPropertyProxyEESide`所有的介面會傳回此介面。 呼叫[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)若要取得[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)介面。 呼叫[QueryInterface](/cpp/atl/queryinterface)上[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)介面，以取得[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 `IEEDataStorage`介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|擷取指定之提供的緩衝區的資料位元組數目。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|擷取可用的資料位元組數目。|  
  
## <a name="remarks"></a>備註  
 此介面的類型視覺化檢視來存取特定物件所持有的資料。 資料會被視為位元組陣列，讓類型視覺化檢視，來操作方式都需要呈現給使用者。  
  
 自訂檢視器也可以使用這個介面，如有需要，通常是自訂檢視器會使用一種自訂介面，雖然[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)或是[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) （適用於字串導向的資料）。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件：Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)