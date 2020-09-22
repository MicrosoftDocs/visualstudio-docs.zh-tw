---
title: 顯示區域變數 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838878"
---
# <a name="displaying-locals"></a>顯示區域變數
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 執行一律會在方法的內容中進行，也就是包含方法或目前的方法。 當執行暫停時，Visual Studio 會呼叫 debug 引擎 (DE) 來取得區域變數和引數的清單，統稱為方法的區域變數。 Visual Studio 會在 [ **區域變數** ] 視窗中顯示這些區域變數和其值。  
  
 若要顯示區域變數，DE 會呼叫屬於 EE 的 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 方法，並為其提供評估內容，也就是符號提供者 (SP) 、目前的執行位址和系結器物件。 如需詳細資訊，請參閱 [評估內容](../../extensibility/debugger/evaluation-context.md)。 如果呼叫成功，則 `IDebugExpressionEvaluator::GetMethodProperty` 方法會傳回 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，代表包含目前執行位址的方法。  
  
 DE 會呼叫 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 來取得 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 物件，此物件經過篩選後只會傳回區域變數並列舉，以產生 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 結構的清單。 每個結構都包含本機的名稱、類型和值。 類型和值會儲存為格式化字串，適用于顯示。 名稱、類型和值通常會一起顯示在 [ **區域變數** ] 視窗的一行中。  
  
> [!NOTE]
> [**快速****監看式] 和 [監看式]** 視窗也會顯示名稱、值和類型相同格式的變數。 不過，這些值是藉由呼叫 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 來取得，而不是藉由呼叫 `IDebugProperty2::EnumChildren` 。  
  
## <a name="in-this-section"></a>本節內容  
 [區域變數的範例實作](../../extensibility/debugger/sample-implementation-of-locals.md)  
 使用範例逐步完成執行區域變數的程式。  
  
## <a name="related-sections"></a>相關章節  
 [評估內容](../../extensibility/debugger/evaluation-context.md)  
 說明當 debug engine (DE) 呼叫運算式評估工具 (EE) 時，會傳遞三個引數。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
