---
title: "IDebugBinder |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder
helpviewer_keywords: IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3377ade8cc4301e1d8a5be19c5d828755934ce9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder"></a>IDebugBinder
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 這個介面會繫結 [符號] 欄位中，通常是傳回的符號提供者，記憶體內容或包含符號的目前值的物件。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 此介面支援運算式評估，而且必須由偵錯引擎 (DE) 實作。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 此介面運算式評估所使用，而且通常用於實作[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)和[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugBinder`。  
  
|方法|描述|  
|------------|-----------------|  
|[繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)|取得的記憶體內容或包含符號的目前值的物件。|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|決定物件的執行階段類型。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|將記憶體內容物件的位置或記憶體位址。|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|取得[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)用來建立函式參數的物件。|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|取得變數的確切類型。|  
  
## <a name="remarks"></a>備註  
 此介面會傳回所使用的運算式評估工具中的物件只有剖析樹狀目錄。 運算式評估工具剖析運算式所使用的符號提供者的執行個體轉換成運算式中的符號[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)，描述根據其類型和位置的原始程式碼中的每個符號。 [繫結](../../../extensibility/debugger/reference/idebugbinder-bind.md)方法轉換`IDebugField`物件加入至[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)連接或繫結符號的物件類型為記憶體中的實際值。 這些`IDebugObject`物件然後會儲存供稍後評估剖析樹狀目錄中。  
  
## <a name="requirements"></a>需求  
 標頭： ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [運算式評估介面](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)