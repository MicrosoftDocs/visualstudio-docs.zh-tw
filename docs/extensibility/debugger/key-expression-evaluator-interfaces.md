---
title: 鍵運算式賦值器介面 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, interfaces
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01527edac4000f0b2f7b89fdd507fc093f0d7734
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738485"
---
# <a name="key-expression-evaluator-interfaces"></a>鍵運算式賦值器介面
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 編寫運算式賦值器 (EE) 以及計算上下文時,應熟悉以下介面。

## <a name="interface-descriptions"></a>介面描述

- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)

     具有單個方法[GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md),它獲取表示當前執行點的數據結構。 此資料結構是調試引擎 (DE) 傳遞給[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)方法以評估表達式的三個參數之一。 此介面通常由符號提供程序實現。

- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)

     具有[Bind](../../extensibility/debugger/reference/idebugbinder-bind.md)方法,該方法獲取包含符號當前值的記憶體區域。 給定包含方法(由[IDebugObject 物件](../../extensibility/debugger/reference/idebugobject.md)表示)和符號本身(由[IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件表示)`IDebugBinder::Bind`都會返回符號的值。 `IDebugBinder`通常由 DE 實現。

- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)

     表示簡單的數據類型。 對於更複雜的類型(如陣列和方法),分別使用派生的[IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md)和[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)介面。 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)是另一個重要的派生介面,它表示包含其他符號(如方法或類)的符號。 介面`IDebugField`(及其衍生物)通常由符號提供程序實現。

     對`IDebugField`象 可用於查找符號的名稱和類型,並且與[IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)物件一起可用於查找其值。

- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)

     表示符號的運行時值的實際位。 [繫結](../../extensibility/debugger/reference/idebugbinder-bind.md)[以 IDebugField](../../extensibility/debugger/reference/idebugfield.md)物件,該物件表示符號,並傳[回 IDebugObject 物件](../../extensibility/debugger/reference/idebugobject.md)。 [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md)方法返回記憶體緩衝區中符號的值。 DE 通常實現此介面以表示記憶體中屬性的值。

- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)

     此介面表示表達式賦值器本身。 鍵方法是[Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md),它傳回[IDebugparsed 運算式](../../extensibility/debugger/reference/idebugparsedexpression.md)介面。

- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)

     此介面表示可供計算的已解析表達式。 鍵方法是[評估同步](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md),它返回表示表達式的值和類型的 IDebugProperty2。

- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)

     此介面表示值及其類型,是表達式計算的結果。

## <a name="see-also"></a>另請參閱
- [評估上下文](../../extensibility/debugger/evaluation-context.md)
