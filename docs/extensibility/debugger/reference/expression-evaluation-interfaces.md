---
title: 運算式評估介面 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736949"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 以下是調試 SDK[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]的運算式評估介面。

## <a name="discussion"></a>討論區
 這些介面用於在中斷模式下計算調用堆疊中的運算式。 它們僅為通用語言運行時表達式賦值器 (EE) 實現。

 表中的每個介面都顯示可以從以下清單中實現它的元件:

- 除錯引擎 (DE)

- 運算式賦值器 (EE)

- 視覺工作室 (VS)

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|表示變數的數字別名。|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|表示變數的數位別名,並使表達式賦值器 (EE) 能夠獲取別名的應用程式域。|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|表示陣列物件。|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|表示託管陣列物件,並允許表達式賦值器 (EE) 確定陣列的基本索引(下限)。|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|表示將調試符號綁定到記憶體中的實際位址的活頁夾。|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|與[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面相同,但提供對類型、別名和自定義可視化工具的訪問。|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|代表運算式評估工具。|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|表示表達式賦值器 (EE) 的增強版本。|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|表示具有增強解析器樹的表達式賦值器 (EE)。|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|表示函數。|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|表示函數並增強[IDebug 函數物件](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|使運算式賦值器 (EE) 能夠在除錯器的輸出視窗中顯示消息。|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|表示託管代碼物件。|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|表示綁定到記憶體位址的任何符號的基介面。|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|與[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面相同,但提供對附加資訊的訪問。|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|表示可供計算的已解析表達式。|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|表示指標。|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|表示解析樹中的指標,並擴展**IDebugPointerObject**介面。|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|提供透過類型視覺化工具修改類型值的能力。|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|提供對自定義查看器和類型可視化工具的訪問。|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|提供創建[IEE 視覺化服務](../../../extensibility/debugger/reference/ieevisualizerservice.md)物件的能力。|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|表示[IDebugObject 物件](../../../extensibility/debugger/reference/idebugobject.md)的集合。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [撰寫 CLR 運算式評估工具](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
