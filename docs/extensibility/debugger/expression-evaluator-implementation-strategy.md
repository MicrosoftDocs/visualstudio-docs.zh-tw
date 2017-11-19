---
title: "運算式評估工具實作策略 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40b97c53570362c79bf3b1627ad183dcf6964b9c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluator-implementation-strategy"></a>運算式評估工具實作策略
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 若要快速建立的運算式評估工具 (EE) 的其中一個方法是先實作最小的程式碼顯示本機變數中的所需**區域變數**視窗。 對於要了解中的每一行**區域變數**視窗會顯示名稱、 類型和值的區域變數，並全部三個都由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件。 名稱、 類型和本機變數的值可以取自`IDebugProperty2`物件藉由呼叫其[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 如需有關如何顯示中的區域變數**區域變數**視窗中，請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)。  
  
## <a name="discussion"></a>討論  
 可能的實作順序開頭實作[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)。 [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)和[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)方法需要實作，以顯示 [區域變數]。 呼叫`IDebugExpressionEvaluator::GetMethodProperty`傳回`IDebugProperty2`物件，代表一種方法： 也就是[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)物件。 方法本身不會顯示在**區域變數**視窗。  
  
 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)接下來應該實作方法。 偵錯引擎 (DE) 呼叫此方法來取得本機變數和引數的清單傳遞`IDebugProperty2::EnumChildren``guidFilter`引數的`guidFilterLocalsPlusArgs`。 `IDebugProperty2::EnumChildren`呼叫[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)和[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)，結合在單一的列舉中的結果。 請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [實作運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)