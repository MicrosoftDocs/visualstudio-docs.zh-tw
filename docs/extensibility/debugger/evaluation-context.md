---
title: 評估內容 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266fe85bedeea2c7e3dae7726d113d66a4b2b1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-context"></a>評估內容
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當偵錯引擎 (DE) 呼叫時，運算式評估工具 (EE) 時，三個引數傳遞至[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)決定尋找及評估符號的內容下, 表所示。  
  
## <a name="arguments"></a>引數  
  
|引數|描述|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)用來識別符號的介面，可指定符號處理常式 (SH)。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)介面，可指定目前執行點。 這可以用來尋找包含正在執行的程式碼的方法。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)可用來尋找的值和指定之名稱的符號類型的介面。|  
  
 `IDebugParsedExpression::EvaluateSync` 傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)代表所產生的值和其類型的介面。  
  
## <a name="see-also"></a>另請參閱  
 [索引鍵運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [顯示 [區域變數]](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)