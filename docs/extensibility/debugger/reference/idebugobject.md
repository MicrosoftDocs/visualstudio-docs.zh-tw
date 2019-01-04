---
title: IDebugObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b10e14d310d5b5b259f696df63ce899765538a94
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889653"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面表示繫結器建立封裝的符號和運算式值的物件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugObject : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 運算式評估工具會實作這個介面來代表的物件。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 這個介面是運算式評估工具會使用已剖析的運算式中的所有物件的基底類別。 它由呼叫[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法。 [QueryInterface](/cpp/atl/queryinterface)從這個介面取得更具特製化的介面。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugObject`。  
  
|方法|描述|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|取得物件的大小。|  
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|取得物件的值做為一系列連續的位元組。|  
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|設定物件的值從一系列連續的位元組。|  
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|設定參考值，這個物件。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|取得代表物件的值的位址的記憶體內容。|  
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|偵錯引擎的位址空間中建立受管理物件的複本。|  
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|測試這個物件是否為 null 參考。|  
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|比較這個物件。|  
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|判斷這個物件是否為唯讀。|  
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|判斷物件是否為透明 proxy。|  
  
## <a name="remarks"></a>備註  
 運算式評估工具會使用此介面的基底類別來代表剖析樹狀結構中的物件。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)   
 [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)