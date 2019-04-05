---
title: IDebugBinder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7f5d1e6786d0d774b658484cf833eee269a1453
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58940449"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會繫結 [符號] 欄位中，通常會傳回符號提供者，記憶體內容或包含符號的目前值的物件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者的附註  
 此介面支援運算式評估，而且必須由偵錯引擎 (DE) 實作。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 此介面用在運算式評估過程中，而且通常用於實作[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)並[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBinder`。  
  
|方法|描述|  
|------------|-----------------|  
|[Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)|取得的記憶體內容或包含符號的目前值的物件。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|決定執行階段類型的物件。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|記憶體內容會將物件的位置或記憶體位址。|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|取得[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的物件。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|取得變數的確切型別。|  
  
## <a name="remarks"></a>備註  
 此介面會傳回物件所使用的運算式評估工具中剖析樹狀結構。 運算式評估工具剖析運算式所使用的符號提供者將轉換的執行個體中的運算式中的符號[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)，可描述以其類型及位置的原始程式碼中的每個符號。 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法將`IDebugField`物件來[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)連接或繫結符號的物件類型的記憶體中的實際值。 這些`IDebugObject`物件接著會儲存在稍後評估的剖析樹狀結構。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間：Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
