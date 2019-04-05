---
title: 索引鍵運算式評估工具介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39dc13c1cc1960b0b5cad6c88b2617ea326e7875
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58942786"
---
# <a name="key-expression-evaluator-interfaces"></a>主要的運算式評估工具介面
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  在 Visual Studio 2015 中，這種實作運算式評估工具已被取代。 如需實作 CLR 運算式評估工具的資訊，請參閱[CLR 運算式評估工具](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)並[Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 在撰寫運算式評估工具 (EE)，以及評估內容，您應該熟悉下列介面。  
  
## <a name="interface-descriptions"></a>介面描述  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     具有單一方法[GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)，此 cmdlet 會取得的資料結構，表示目前執行點。 此資料結構是一個偵錯引擎 (DE) 傳遞給三個引數[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)方法來評估運算式。 符號提供者通常被實作這個介面。  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     已[繫結](../../extensibility/debugger/reference/idebugbinder-bind.md)方法，取得包含目前的符號值的記憶體區域。 指定這兩個包含方法，由[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件，而符號本身，由[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件，`IDebugBinder::Bind`傳回符號的值。 `IDebugBinder` 通常是由 DE 實作。  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     表示簡單的資料類型。 對於更複雜的類型，例如陣列和方法，使用衍生[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)並[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)分別介面。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)是另一個重要的衍生的介面，表示包含其他符號，例如方法或類別的符號。 `IDebugField`介面 （和其衍生項目） 通常由符號提供者實作。  
  
     `IDebugField`物件可以用來尋找符號的類型與名稱，連同[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)物件，可用來尋找其值。  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     代表實際的位元執行階段值的符號。 [繫結](../../extensibility/debugger/reference/idebugbinder-bind.md)會採用[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件，代表一種符號，並且傳回[IDebugObject](../../extensibility/debugger/reference/idebugobject.md)物件。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)方法會傳回符號的值在記憶體緩衝區。 DE 通常會實作這個介面來表示記憶體中的屬性的值。  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     此介面代表運算式評估工具本身。 重要的方法是[剖析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)，以傳回[IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)介面。  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     這個介面會表示準備要評估的已剖析的運算式。 重要的方法是[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) IDebugProperty2 會傳回代表的值和運算式的類型。  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     此介面代表的值和型別，而是運算式評估的結果。  
  
## <a name="see-also"></a>另請參閱  
 [評估內容](../../extensibility/debugger/evaluation-context.md)
