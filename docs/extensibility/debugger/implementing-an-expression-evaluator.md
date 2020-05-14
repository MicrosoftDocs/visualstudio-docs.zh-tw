---
title: 實現運算式賦值器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8c7c9a1130794dd4c28f212afd6cb3c030f5a1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738548"
---
# <a name="implement-an-expression-evaluator"></a>實作式賦值器
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 計算運算式是除錯引擎 (DE)、符號提供者 (SP)、活頁夾物件和運算式賦值器 (EE) 之間的複雜相互作用。 這四個元件由一個元件實現並由另一個元件使用的介面連接。

 EE 以字串的形式從 DE 獲取運算式,並對其進行解析或計算。 EE 執行以下介面,DE 使用這些介面:

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

  EE 呼叫 DE 提供的活頁夾物件,以獲得符號和物件的值。 EE 使用以下介面,這些介面由 DE 實現:

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)

- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)

- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)

- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)

- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

  EE 執行[IDebugproperty2](../../extensibility/debugger/reference/idebugproperty2.md)。 `IDebugProperty2`提供用於描述運算式計算結果的機制,例如局部變數、基元或 Visual Studio 的物件,然後該函數在 **「局部變數**」、**監視**或 **「立即」** 視窗中顯示相應的資訊。

  當 DE 要求提供資訊時,它向 EE 授予該 SP。 SP 執行描述位址和欄位的介面,例如以下介面及其衍生物:

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE 會使用所有這些介面。

## <a name="in-this-section"></a>本節內容
 [運算式賦值器實現策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)為表達式賦值器 (EE) 實施策略定義三步過程。

## <a name="see-also"></a>另請參閱
- [編寫 CLR 表示式賦值器](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
