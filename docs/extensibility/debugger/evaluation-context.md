---
title: 評估內容 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b48d38b533fc53724ec7b9da6b7608a01f8fcd24
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038405"
---
# <a name="evaluation-context"></a>評估內容
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 當偵錯引擎 (DE) 呼叫運算式評估工具 (EE)，三個引數，傳遞給[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)判斷尋找及評估符號的內容下, 表所示。  
  
## <a name="arguments"></a>引數  
  
|引數|描述|  
|--------------|-----------------|  
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)用來識別符號的介面，可指定的符號處理常式 (SH)。|  
|`pAddress`|[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)介面，可指定目前執行點。 這個介面會尋找包含正在執行的程式碼的方法。|  
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)找到的值和類型指定名稱的符號的介面。|  
  
 `IDebugParsedExpression::EvaluateSync` 會傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面，表示產生的值和型別。  
  
## <a name="see-also"></a>另請參閱  
 [索引鍵運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)