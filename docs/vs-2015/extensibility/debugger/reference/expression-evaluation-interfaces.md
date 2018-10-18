---
title: 運算式評估介面 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2362f0000ece6377a3dc2022e73afcc2fd024000
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262284"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 以下是針對的運算式評估介面[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]偵錯 sdk 》。  
  
## <a name="discussion"></a>討論  
 這些介面用來評估在中斷模式期間的呼叫堆疊中的運算式。 它們只針對通用語言執行階段運算式評估工具 (EE) 進行實作。  
  
 在資料表中的每個介面會顯示可以實作下列清單中的元件：  
  
-   偵錯引擎 (DE)  
  
-   運算式評估工具 (EE)  
  
-   Visual Studio (VS)  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|表示變數的數字的別名。|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|代表數值的別名的變數，並可讓運算式評估工具 (EE) 來取得應用程式定義域做為別名。|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|表示陣列物件。|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|表示 managed 的陣列物件，並可讓運算式評估工具 (EE) 來判斷陣列的基底的索引 （下限）。|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|表示繫結偵錯符號，可在記憶體中的實際位址的繫結器。|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|與相同[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)介面但能夠存取型別、 別名和自訂視覺化檢視。|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|代表運算式評估工具。|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|表示的運算式評估工具 (EE) 的增強型的版本。|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|表示的運算式評估工具 (EE) 與增強的剖析器樹狀目錄。|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|表示函式。|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|表示函式，並增強[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)介面。|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|可讓運算式評估工具 (EE)，才能偵錯工具的 [輸出] 視窗中顯示一則訊息。|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|代表 managed 程式碼的物件。|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|基底介面中的所有符號表示繫結至記憶體位址。|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|與相同[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)介面但可提供其他資訊的存取權。|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|表示剖析準備要評估的運算式。|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|表示的指標。|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|表示剖析樹狀結構中的指標，並延伸**IDebugPointerObject**介面。|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|讓您能夠修改透過類型視覺化檢視類型的值。|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|提供存取自訂檢視器和類型視覺化檢視。|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|讓您能夠建立[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)物件。|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|表示的集合[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)物件。|  
  
## <a name="see-also"></a>另請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [撰寫 CLR 運算式評估工具](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [類型視覺化檢視和自訂檢視器](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

