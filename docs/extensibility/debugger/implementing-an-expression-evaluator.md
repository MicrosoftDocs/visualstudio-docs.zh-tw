---
title: 執行運算式評估工具 |Microsoft Docs
description: 瞭解如何評估運算式，其中牽涉到 debug engine、symbol provider、系結器物件和運算式評估工具。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121bd17e2343cfbba509e85d78ba37b57964f895
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947667"
---
# <a name="implement-an-expression-evaluator"></a>執行運算式評估工具
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 評估運算式是偵錯工具引擎 (DE) 、符號提供者 (SP) 、系結器物件，以及運算式評估工具 (EE) 之間的複雜相互作用。 這四個元件是由一個元件所執行並由另一個元件所使用的介面所連接。

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

  EE 會執行 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)。 `IDebugProperty2` 提供用來描述運算式評估結果的機制，例如區域變數、基本或要 Visual Studio 的物件，然後在 [ **區域變數**]、 **[監看** 式] 或 [即時運算 **] 視窗中** 顯示適當的資訊。

  當您要求資訊時，會將 SP 指定給 EE。 SP 會執行描述位址和欄位的介面，例如下列介面及其衍生項：

- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

  EE 會取用所有這些介面。

## <a name="in-this-section"></a>本節內容
 [運算式評估工具執行策略](../../extensibility/debugger/expression-evaluator-implementation-strategy.md) 定義運算式評估工具 (EE) 實行策略的三步驟處理。

## <a name="see-also"></a>另請參閱
- [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
