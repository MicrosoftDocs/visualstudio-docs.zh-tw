---
title: 執行運算式評估工具 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838846"
---
# <a name="implementing-an-expression-evaluator"></a>實作運算式評估工具
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。  
  
 評估運算式是偵錯工具引擎 (DE) 、符號提供者 (SP) 、系結器物件，以及運算式評估工具 (EE) 本身之間的複雜相互作用。 這四個元件是由一個元件所執行並由另一個元件所使用的介面所連接。  
  
 EE 會採用字串形式的 DE 運算式，並加以剖析或評估。 此 EE 會執行下列介面，這些介面會由 DE 所耗用：  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE 會呼叫由 DE 提供的系結器物件，以取得符號和物件的值。 EE 會取用下列介面，這些介面會由 DE 來執行：  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  EE 會實行 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)。 `IDebugProperty2` 提供用來描述運算式評估結果的機制，例如區域變數、基本型別或物件，以 Visual Studio，然後在 [ **區域變數**]、 **[監看**式] 或 [即時 **運算] 視窗** 中顯示適當的資訊。  
  
  當您要求資訊時，會將 SP 指定給 EE。 SP 會執行描述位址和欄位的介面，例如下列介面和其衍生項：  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE 會取用所有這些介面。  
  
## <a name="in-this-section"></a>本節內容  
 [運算式評估工具的實作策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 定義運算式評估工具 (EE) 實行策略的三步驟處理。  
  
## <a name="see-also"></a>另請參閱  
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
