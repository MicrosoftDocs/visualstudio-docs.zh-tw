---
title: 運算式評估工具執行策略 |Microsoft Docs
description: 深入瞭解建立運算式評估工具的策略，方法是先執行程式碼，以在 [區域變數] 視窗中顯示本機變數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d7527c361a889d5aa1f19ec7a211f8aeb8dcbd15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921379"
---
# <a name="expression-evaluator-implementation-strategy"></a>運算式評估工具執行策略
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 快速建立運算式評估工具 (EE) 的其中一種方法是先執行在 [ **區域變數** ] 視窗中顯示本機變數所需的最少程式碼。 請注意，[ **區域變數** ] 視窗中的每一行都會顯示區域變數的名稱、類型和值，而且全部三個都是以 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件表示。 區域變數的名稱、類型和值是藉 `IDebugProperty2` 由呼叫其 [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 方法，從物件取得的。 如需有關如何在 [ **區域變數** ] 視窗中顯示本機變數的詳細資訊，請參閱 [顯示區域變數](../../extensibility/debugger/displaying-locals.md)。

## <a name="discussion"></a>討論
 可能的實行順序從實 [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)開始。 必須實作為 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 和 [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) 方法來顯示區域變數。 呼叫 `IDebugExpressionEvaluator::GetMethodProperty` 會傳回 `IDebugProperty2` 代表方法的物件：也就是 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) 物件。 方法本身不會顯示在 [ **區域變數** ] 視窗中。

 接下來應執行 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 方法。 Debug engine (DE) 呼叫這個方法，藉由傳遞的引數來取得區域變數和引數的清單 `IDebugProperty2::EnumChildren` `guidFilter` `guidFilterLocalsPlusArgs` 。 `IDebugProperty2::EnumChildren` 呼叫 [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 和 [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)，並將結果合併成單一列舉。 如需詳細資料，請參閱 [顯示區域變數](../../extensibility/debugger/displaying-locals.md) 。

## <a name="see-also"></a>另請參閱
- [執行運算式評估工具](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)
