---
title: 運算式評估 (Visual Studio 偵錯 SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52c897e40b825f85e07b4b4f14796655618280a8
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230730"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>運算式評估 (Visual Studio 偵錯 SDK)
在中斷模式中，IDE 必須評估涉及數個程式變數的簡單運算式。 若要完成其評估，偵錯引擎 (DE) 必須剖析並評估在其中一個 IDE 視窗中輸入的運算式。 
  
 運算式會建立具有[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法和所產生代表[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面。  
  
 **IDebugExpression2**介面的實作方法 DE 並呼叫其**EvalAsync**方法，以傳回[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ide，以顯示介面在 IDE 中的運算式評估的結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)傳回的結構，用來放置到運算式的值**監看式**視窗或 into**區域變數**視窗。  
  
 偵錯封裝或工作階段偵錯管理員 (SDM) 會呼叫[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)或是[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)若要取得[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)表示介面評估的結果。 `IDebugProperty2` 有方法會傳回名稱、 類型和運算式的值。 這項資訊會出現在各種不同的偵錯工具視窗。  
  
## <a name="using-expression-evaluation"></a>使用運算式評估  
 若要使用運算式的評估版，您必須實作[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法，以及所有的方法[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)介面下, 表所示。  
  
|方法|描述|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估運算式。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步運算式評估。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式來評估運算式。|  
  
 同步和非同步評估需要實作[IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 非同步運算式評估要求實作[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)。  
  
## <a name="see-also"></a>另請參閱  
 [執行控制和狀態評估](../../extensibility/debugger/execution-control-and-state-evaluation.md)