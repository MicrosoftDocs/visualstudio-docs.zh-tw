---
title: IDebugMethodField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField
helpviewer_keywords:
- IDebugMethodField interface
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba7ea690cdf89bd76474ddb0e863b629137e7242
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922464"
---
# <a name="idebugmethodfield"></a>IDebugMethodField
此介面描述的方法。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 符號提供者所實作的相同物件上實作這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面。 這個介面是提供一種方法的特製化。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 使用[QueryInterface](/cpp/atl/queryinterface)若要取得從這個介面[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)傳回`FIELD_TYPE_METHOD`。 此外，這些方法中， [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)， [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)，並[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)，則傳回所有`IDebugMethodField`介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 上的方法除了[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)並[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)介面，這個介面會實作下列方法：  
  
|方法|描述|  
|------------|-----------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|建立的列舉程式方法的參數。|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|取得物件，包含方法的"this"指標。|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|建立方法的所有區域變數的列舉值。|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|建立選取的本機變數之方法的列舉值。|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|判斷是否已定義特定的自訂屬性。|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|建立方法的靜態區域變數的列舉值。|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|取得方法的通用的容器。|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|建立的每一個需要呼叫方法的引數類型的列舉值。|  
  
## <a name="remarks"></a>備註  
 一種方法可以包含參數，以及本機變數。  
  
## <a name="requirements"></a>需求  
 標頭： sh.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [符號提供者介面](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)