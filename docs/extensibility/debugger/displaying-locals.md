---
title: 顯示區域變數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 50e6c7d74f522865098ef9b4262dd71e460720a2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922307"
---
# <a name="display-locals"></a>顯示 [區域變數]
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 實作 CLR 運算式評估工具的詳細資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 永遠執行的方法，也就是包含的方法或目前的方法內容中進行。 當執行暫停時，Visual Studio 會呼叫偵錯引擎 (DE) 取得一份本機變數和引數，統稱為方法的區域變數。 Visual Studio 會顯示這些區域變數和其值在**區域變數**視窗。  
  
 若要顯示區域變數，呼叫 DE [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)屬於 EE 方法並為其提供的評估內容，、 符號提供者 (SP)、 目前的執行位址和繫結器物件。 如需詳細資訊，請參閱 <<c0> [ 評估內容](../../extensibility/debugger/evaluation-context.md)。 如果呼叫成功，`IDebugExpressionEvaluator::GetMethodProperty`方法會傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，表示包含目前執行位址的方法。  
  
 DE 呼叫[EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)若要取得[IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)物件，它會篩選為傳回唯一的區域變數，並且列舉以產生一份[DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)結構。 每個結構會包含名稱、 類型和區域變數的值。 類型和值會儲存為格式化的字串，適用於顯示。 名稱、 類型和值通常一起顯示在一行**區域變數**視窗。  
  
> [!NOTE]
>  **快速監看式**並**監看式**視窗也會顯示變數的名稱、 值和類型相同的格式。 不過，藉由呼叫以取得這些值[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)而不是`IDebugProperty2::EnumChildren`。  
  
## <a name="in-this-section"></a>本節內容  
 [區域變數的範例實作](../../extensibility/debugger/sample-implementation-of-locals.md)  
 使用範例來逐步完成實作區域變數的程序。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 說明當偵錯引擎 (DE) 呼叫，運算式評估工具 (EE) 時，它會傳遞三個引數。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)