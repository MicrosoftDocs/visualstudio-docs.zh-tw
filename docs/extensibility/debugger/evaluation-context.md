---
title: 評估上下文 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738809"
---
# <a name="evaluation-context"></a>評估內容
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 當調試引擎 (DE) 呼叫表示式賦值器 (EE) 時,傳遞給[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)的三個參數決定了查找和評估符號的上下文,如下表所示。

## <a name="arguments"></a>引數

|引數|描述|
|--------------|-----------------|
|`pSymbolProvider`|[IDebugSymbolProvider 介面](../../extensibility/debugger/reference/idebugsymbolprovider.md),用於指定用於識別符號的符號處理程式 (SH)。|
|`pAddress`|指定目前執行點的[IDebug 位址](../../extensibility/debugger/reference/idebugaddress.md)介面。 此介面查找包含要執行的代碼的方法。|
|`pBinder`|[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)介面,用於查找給定符號名稱的值和類型。|

 `IDebugParsedExpression::EvaluateSync`返回表示結果值及其類型的[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面。

## <a name="see-also"></a>另請參閱
- [鍵運算式賦值器介面](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [顯示本地變數](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
