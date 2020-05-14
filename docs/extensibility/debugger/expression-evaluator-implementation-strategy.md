---
title: 運算式賦值器實現策略 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3922689c20c839b3c0c2b2440bc9fefd5d25c80a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738679"
---
# <a name="expression-evaluator-implementation-strategy"></a>運算式賦值器實現策略
> [!IMPORTANT]
> 在 Visual Studio 2015 中,這種實現表達式賦值器的方式被棄用。 有關實現 CLR 表示式賦值器的資訊,請參閱[CLR 表示式賦值器](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)和[託管運算式賦值器範例](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)。

 快速建立運算式賦值器 (EE) 的一種方法是首先實現在 **「局部變數」** 視窗中顯示局部變數所需的最小程式碼。 必須認識到「**局部變數」** 視窗中的每一行都顯示局部變數的名稱、類型和值,並且所有三行都由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件表示。 局部變數的名稱、類型和值通過調用其[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)`IDebugProperty2`方法從物件獲得。 關於如何在 **「局部變數」** 視窗中顯示局部變數的詳細資訊,請參考[資料 。](../../extensibility/debugger/displaying-locals.md)

## <a name="discussion"></a>討論區
 可能的實現序列從實現[IDebugExpression 賦值器](../../extensibility/debugger/reference/idebugexpressionevaluator.md)開始。 必須實現[分析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)法和[GetMethod Property](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)方法以顯示局部變數。 呼叫`IDebugExpressionEvaluator::GetMethodProperty`傳回`IDebugProperty2`表示方法的物件:即[IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)物件。 方法本身不顯示在 **「局部變數」** 視窗中。

 接下來應實現[枚舉子](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)方法。 除錯引擎 (DE) 呼叫此方法,`IDebugProperty2::EnumChildren`透過`guidFilter``guidFilterLocalsPlusArgs`傳遞的 參數來取得本地變數和參數的清單。 `IDebugProperty2::EnumChildren`調用[枚舉](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)和[枚舉,](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)將結果合併到單個枚舉中。 關於詳細資訊[,請參閱顯示局部變數](../../extensibility/debugger/displaying-locals.md)。

## <a name="see-also"></a>另請參閱
- [實作式賦值器](../../extensibility/debugger/implementing-an-expression-evaluator.md)
- [顯示區域變數](../../extensibility/debugger/displaying-locals.md)
