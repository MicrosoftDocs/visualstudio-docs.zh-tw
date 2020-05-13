---
title: 計算運算式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738823"
---
# <a name="evaluate-expressions"></a>計算運算式
運算式是從從**自動**、**監視**、**快速監視**或**即時**視窗向下傳遞的字串建立的。 計算運算式時,它生成一個可列印字串,其中包含變數或參數的名稱和類型及其值。 此字串顯示在相應的 IDE 視窗中。

## <a name="implementation"></a>實作
 當程式在斷點停止時,將計算表達式。 表達式本身由[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面表示,該介面表示已解析的運算式,該運算式可用於在給定的表達式運算上下文中進行綁定和評估。 堆疊幀確定表達式計算上下文,調試引擎 (DE) 通過實現[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面來提供該上下文。

 給定使用者字串和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面,調試引擎 (DE) 可以透過使用者字串傳遞給[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法來取得[IDebugExpressionExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。 返回的 IDebugExpression2 介面包含可供評估的解析運算式。

 以`IDebugExpression2`此介面,DE可以透過同步或非同步表示式計算獲得表示式的值,使用[IDebugExpression2:::計算同步](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[IDebugExpression2::評估Async](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)。 此值以及變數或參數的名稱和類型將發送到 IDE 進行顯示。 值、名稱和類型由[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)介面表示。

 要啟用運算式計算,DE 必須實現[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)和[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 同步和異步計算都需要[IDebugProperty2:::getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法的實現。

## <a name="see-also"></a>另請參閱
- [堆疊幀](../../extensibility/debugger/stack-frames.md)
- [運算式運算內容](../../extensibility/debugger/expression-evaluation-context.md)
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
