---
title: 評估內容 |Microsoft Docs
description: 當 debug engine 呼叫運算式評估工具時，引數會決定尋找和評估符號的內容： pSymbolProvider、pAddress 和 pBinder。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0957a204a83ab72aabe14fe4a70d8e758e83a08f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840583"
---
# <a name="evaluation-context"></a>評估內容
> [!IMPORTANT]
> 在 Visual Studio 2015 中，這種執行運算式評估工具的方法已被取代。 如需有關執行 CLR 運算式評估工具的詳細資訊，請參閱 [clr 運算式評估](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 工具和 [Managed 運算式評估工具範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 當 debug engine (DE) 呼叫運算式評估工具 (EE) 時，傳遞給 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 的三個引數會決定尋找和評估符號的內容，如下表所示。

## <a name="arguments"></a>引數

|引數|描述|
|--------------|-----------------|
|`pSymbolProvider`|[IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)介面，指定用來識別符號的符號處理常式 (SH) 。|
|`pAddress`|指定目前執行點的 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) 介面。 這個介面會尋找包含要執行之程式碼的方法。|
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面，可尋找指定其名稱的符號值和類型。|

 `IDebugParsedExpression::EvaluateSync` 傳回表示產生的值及其型別的 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 介面。

## <a name="see-also"></a>另請參閱
- [索引鍵運算式評估工具介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
