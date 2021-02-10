---
title: 索引鍵運算式評估工具介面 |Microsoft Docs
description: 瞭解當您撰寫運算式評估工具時應該熟悉的介面，以及評估內容。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95c32b76893e0de7f31e56df81bf12c831452bfe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945925"
---
# <a name="key-expression-evaluator-interfaces"></a>索引鍵運算式評估工具介面
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關如何執行 CLR 運算式評估工具的詳細資訊，請參閱 [CLR 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 當撰寫運算式評估工具 (EE) ，以及評估內容時，您應該熟悉下列介面。

## <a name="interface-descriptions"></a>介面描述

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     具有單一方法 [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md)，它會取得代表目前執行點的資料結構。 此資料結構是 debug engine (DE) 傳遞至 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 方法以評估運算式的三個引數之一。 這個介面通常是由符號提供者所執行。

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     具有 [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) 方法，可取得包含符號目前值的記憶體區域。 假設有兩個包含方法（以 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件表示）和符號本身（以 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件表示），則會傳回 `IDebugBinder::Bind` 符號的值。 `IDebugBinder` 通常是由 DE 所執行。

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     表示簡單的資料類型。 針對更複雜的型別，例如陣列和方法，分別使用衍生的 [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) 和 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 介面。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) 是另一個重要的衍生介面，代表包含其他符號的符號，例如方法或類別。 `IDebugField`介面 (及其衍生) 通常是由符號提供者所執行。

     您 `IDebugField` 可以使用物件來尋找符號的名稱和類型，以及使用 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 物件來尋找其值。

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     代表符號之運行時間值的實際位。 [Bind](../../extensibility/debugger/reference/idebugbinder-bind.md) 會採用代表符號的 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 物件，並傳回 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 物件。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)方法會傳回記憶體緩衝區中的符號值。 DE 通常會執行此介面來代表記憶體中的屬性值。

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     此介面代表運算式評估工具本身。 主要方法是 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)，它會傳回 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) 介面。

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     這個介面表示已剖析的運算式可供評估。 Key 方法是 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ，它會傳回代表運算式值和類型的 IDebugProperty2。

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     此介面代表值和其型別，而且是運算式評估的結果。

## <a name="see-also"></a>另請參閱
- [評估內容](../../extensibility/debugger/evaluation-context.md)
