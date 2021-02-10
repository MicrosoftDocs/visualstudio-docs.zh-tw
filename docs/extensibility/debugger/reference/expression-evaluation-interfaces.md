---
title: 運算式評估介面 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a048d11b09ee873a2f5a11e35db78f68df6ad680
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936934"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 以下是偵錯工具 SDK 的運算式評估介面 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。

## <a name="discussion"></a>討論
 在中斷模式期間，這些介面是用來評估呼叫堆疊中的運算式。 它們只會在 (EE) 的通用語言運行時程表達式評估工具上執行。

 表格中的每個介面都會顯示可從下列清單中執行的元件：

- Debug Engine (DE) 

-  (EE) 的運算式評估工具

- Visual Studio (VS) 

|介面|實作為|Description|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|代表變數的數值別名。|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|代表變數的數值別名，並讓運算式評估工具 (EE) 取得別名的應用程式域。|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|表示陣列物件。|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|代表 managed 陣列物件，並允許運算式評估工具 (EE) 判斷陣列 (下限) 的基底索引。|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|表示系結器，它會將偵錯工具符號系結至記憶體中的實際位址。|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|與 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 介面相同，但可讓您存取類型、別名和自訂的視覺化檢視。|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|代表運算式評估工具。|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|表示 (EE) 的增強版運算式評估工具。|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|表示具有增強型剖析器樹狀結構 (EE) 的運算式評估工具。|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|表示函數。|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|代表函式並增強 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) 介面。|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|讓運算式評估工具 (EE) 在偵錯工具的輸出視窗中顯示訊息。|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|表示 managed 程式碼物件。|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|代表系結至記憶體位址之任何符號的基底介面。|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|與 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 介面相同，但會提供其他資訊的存取權。|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|表示準備要評估的已剖析運算式。|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|表示指標。|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|表示剖析樹狀結構中的指標，並擴充 **IDebugPointerObject** 介面。|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|提供透過型別視覺化程式來修改型別值的功能。|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|提供對自訂檢視器和型別視覺化的存取。|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|提供建立 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 物件的能力。|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|代表 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 物件的集合。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [撰寫 CLR 運算式評估工具](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
