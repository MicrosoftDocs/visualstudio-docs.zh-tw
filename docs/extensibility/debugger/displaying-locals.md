---
title: 顯示 [區域變數] |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03a3f08498e8b046b02defd32083677b7f39e7e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108426"
---
# <a name="displaying-locals"></a>顯示 [區域變數]
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 一律執行會在方法中，也就是包含的方法或目前方法的內容中發生。 當執行暫停時，Visual Studio 會呼叫偵錯引擎 (DE) 取得一份本機變數和引數，統稱為 「 方法的區域變數。 Visual Studio 會顯示這些區域變數和其值在**區域變數**視窗。  
  
 若要顯示 [區域變數]，呼叫 DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)屬於 EE 方法，並讓它的評估內容、 符號提供者 (SP)、 目前的執行位址和繫結器物件。 如需詳細資訊，請參閱[評估內容](../../extensibility/debugger/evaluation-context.md)。 如果呼叫成功，`IDebugExpressionEvaluator::GetMethodProperty`方法會傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，代表包含目前執行位址的方法。  
  
 DE 呼叫[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)取得[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，其篩選為傳回唯一的區域變數，並產生一份列舉[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構。 每個結構會包含名稱、 類型和值的區域變數。 類型和值會儲存為格式化的字串，適用於顯示。 名稱、 類型和值通常會一起在一行中**區域變數**視窗。  
  
> [!NOTE]
>  **快速監看式**和**監看式**視窗也會顯示具有相同格式的名稱、 值和類型的變數。 不過，這些值藉由呼叫中取得[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)而不是`IDebugProperty2::EnumChildren`。  
  
## <a name="in-this-section"></a>本節內容  
 [區域變數的範例實作](../../extensibility/debugger/sample-implementation-of-locals.md)  
 逐步執行實作區域變數的程序會使用範例。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 說明當偵錯引擎 (DE) 呼叫運算式評估工具 (EE) 時，它會傳遞三個引數。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)