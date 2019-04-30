---
title: 運算式評估工具的實作策略 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dabf4406752d04c0beec39d7f5997b09e3a5fc1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409893"
---
# <a name="expression-evaluator-implementation-strategy"></a>運算式評估工具的實作策略
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 若要快速建立的運算式評估工具 (EE) 的其中一個方法是先實作最小的程式碼顯示本機變數中的所需**區域變數**視窗。 您最好了解中的每一行**區域變數** 視窗會顯示名稱、 類型和值的區域變數，且所有三個都由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件。 名稱、 類型和本機變數的值取自`IDebugProperty2`物件，藉由呼叫其[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 如需有關如何顯示在中的區域變數**區域變數** 視窗中，請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)。

## <a name="discussion"></a>討論
 可能的實作順序開始實作[IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)。 [剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)並[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)必須實作的方法，以顯示區域變數。 呼叫`IDebugExpressionEvaluator::GetMethodProperty`會傳回`IDebugProperty2`物件，表示一種方法： 亦即[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)物件。 方法本身不會顯示在**區域變數**視窗。

 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)接下來應該實作方法。 偵錯引擎 (DE) 呼叫此方法來取得本機變數和引數的清單，藉由傳遞`IDebugProperty2::EnumChildren``guidFilter`引數`guidFilterLocalsPlusArgs`。 `IDebugProperty2::EnumChildren` 呼叫[EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)並[EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)，結合在單一的列舉型別結果。 請參閱[顯示區域變數](../../extensibility/debugger/displaying-locals.md)如需詳細資訊。

## <a name="see-also"></a>另請參閱
- [實作運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [顯示 [區域變數]](../../extensibility/debugger/displaying-locals.md)