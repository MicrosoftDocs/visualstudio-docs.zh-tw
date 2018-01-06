---
title: "索引鍵運算式評估工具介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1e0d655f18ec7ec50dffa52e3ac4ce363fb02fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="key-expression-evaluator-interfaces"></a>索引鍵運算式評估工具介面
> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在撰寫及評估內容的運算式評估工具 (EE，)，您應該熟悉下列介面。  
  
## <a name="interface-descriptions"></a>介面描述  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     具有單一方法[GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)，此 cmdlet 會取得的資料結構，代表目前執行點。 這個資料結構是偵錯引擎 (DE) 傳遞給三個引數的其中一個[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)方法來評估運算式。 符號提供者通常會實作這個介面。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     具有[繫結](../../extensibility/debugger/reference/idebugbinder-bind.md)方法，取得包含目前的符號值的記憶體區域。 指定這兩個包含的方法，由[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件和符號本身，由[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件`IDebugBinder::Bind`傳回符號的值。 `IDebugBinder`通常是由 DE 實作。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     表示簡單資料類型。 對於更複雜的類型，例如陣列和方法，使用衍生[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)和[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)分別介面。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)是另一個重要的衍生的介面，表示包含其他符號，例如方法或類別的符號。 `IDebugField`介面 （和其衍生項目） 通常由符號提供者實作。  
  
     `IDebugField`物件可以用來尋找符號類型與名稱，連同[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)物件，可以用來尋找其值。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     代表實際的位元執行階段值的符號。 [繫結](../../extensibility/debugger/reference/idebugbinder-bind.md)採用[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件，代表一種符號，並且傳回[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)方法會傳回符號的值中的記憶體緩衝區。 DE 通常會實作這個介面來表示記憶體中的屬性的值。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     此介面代表運算式評估工具本身。 主要方法是[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)，它會傳回[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)介面。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     此介面代表剖析準備要評估的運算式。 主要方法是[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) IDebugProperty2 會傳回代表的值和運算式的類型。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     此介面代表值和其類型，而且是運算式評估的結果。  
  
## <a name="see-also"></a>請參閱  
 [評估內容](../../extensibility/debugger/evaluation-context.md)