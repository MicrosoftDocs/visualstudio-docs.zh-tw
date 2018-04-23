---
title: 運算式評估工具 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dd2cc4409dbdb7650454715e133fd76dda5b780
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator"></a>運算式評估工具
運算式評估工具 (EE) 檢查語言剖析和執行階段，在評估變數和運算式的語法讓 IDE 處於中斷模式時，使用者可以檢視它們。  
  
## <a name="using-expression-evaluators"></a>使用運算式評估工具  
 運算式建立使用[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，如下所示：  
  
1.  偵錯引擎 (DE) 實作[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。  
  
2.  偵錯封裝取得`IDebugExpressionContext2`物件從[IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)介面，然後呼叫`IDebugStackFrame2::ParseText`方法上，以取得[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)物件。  
  
3.  偵錯封裝呼叫[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法或[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法來取得運算式的值。 `IDebugExpression2::EvaluateAsync` 從命令/即時運算視窗呼叫。 所有其他的 UI 元件呼叫`IDebugExpression2::EvaluateSync`。  
  
4.  運算式評估的結果是[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)物件，其中包含名稱、 類型和值的運算式評估的結果。  
  
 在運算式評估期間 EE 會需要從符號提供者元件的資訊。 符號提供者會提供用於識別並了解剖析的運算式的符號資訊。  
  
 完成非同步的運算式評估時，就會由工作階段的偵錯管理員 (SDM) 透過 DE 非同步事件傳送至通知 IDE 運算式評估已完成。 同步的運算式評估完成時，從呼叫傳回評估的結果`IDebugExpression2::EvaluateSync`方法。  
  
## <a name="implementation-notes"></a>實作注意事項  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎預期要與運算式評估工具使用 Common Language Runtime (CLR) 介面。 因此，運算式評估工具適用於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]偵錯引擎都必須支援的 CLR (所有 CLR 偵錯介面的完整清單位於 debugref.doc 屬於的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)])。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具元件](../../extensibility/debugger/debugger-components.md)