---
title: 運算式評估工具 |Microsoft Docs
description: 瞭解運算式評估工具，其會檢查語言的語法，以在執行時間于中斷模式中剖析和評估變數和運算式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8223e39eb804684fede50ceb2f7c859e198a272
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560131"
---
# <a name="expression-evaluator"></a>運算式評估工具
運算式評估工具 (EE) 檢查語言的語法，以在執行時間剖析和評估變數和運算式，讓使用者可以在 IDE 處於中斷模式時，讓使用者查看。

## <a name="use-expression-evaluators"></a>使用運算式評估工具
 運算式會使用 [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 方法建立，如下所示：

1. Debug engine (DE) 會實 [IDebugExpressionCoNtext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) 介面。

2. Debug 封裝 `IDebugExpressionContext2` 會從 [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) 介面取得物件，然後 `IDebugStackFrame2::ParseText` 在其上呼叫方法以取得 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 物件。

3. Debug 封裝會呼叫 [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 方法或 [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 方法來取得運算式的值。 `IDebugExpression2::EvaluateAsync` 從命令/即時運算視窗呼叫。 所有其他 UI 元件 `IDebugExpression2::EvaluateSync` 的呼叫。

4. 運算式評估的結果是 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) 物件，其中包含運算式評估結果的名稱、類型和值。

   在運算式評估期間，EE 需要來自符號提供者元件的資訊。 符號提供者會提供用來識別和瞭解剖析之運算式的符號資訊。

   當非同步運算式評估完成時，會透過會話 debug manager (SDM) 來傳送非同步事件，以通知 IDE 運算式評估已完成。 然後，評估的結果會從對方法的呼叫傳回 `IDebugExpression2::EvaluateSync` 。

## <a name="implementation-notes"></a>實作附註
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debug engine 預期會使用 Common Language Runtime (CLR) 介面來與運算式評估工具交談。 因此，搭配 debug 引擎使用的運算式評估工具 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 必須支援 clr (所有 clr 偵錯工具的完整清單可以在 debugref.doc （) 的一部分）中找到 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] 。

## <a name="see-also"></a>另請參閱
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
