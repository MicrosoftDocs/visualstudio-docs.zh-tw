---
title: "IDebugExpression2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2
helpviewer_keywords: IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ba89642b51d4b1d471bc6c46d84441c6383005c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2"></a>IDebugExpression2
此介面代表繫結和評估剖析的運算式已備妥。  
  
## <a name="syntax"></a>語法  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>實作者注意事項  
 偵錯引擎 (DE) 會實作這個介面來代表剖析準備要評估的運算式。  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)傳回此介面。 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 只有在已暫停，正在偵錯的程式，並堆疊框架是可用時，這些介面是可存取。  
  
## <a name="methods-in-vtable-order"></a>依照 Vtable 順序的方法  
 下表顯示的方法`IDebugExpression2`。  
  
|方法|說明|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|以非同步方式評估此運算式。|  
|[中止](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|結束非同步的運算式評估。|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|以同步方式會評估此運算式。|  
  
## <a name="remarks"></a>備註  
 已停止執行程式，當工作階段的偵錯管理員 (SDM) 會從呼叫 DE 取得堆疊框架[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)。 然後呼叫 SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)取得[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。 後面接著呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)建立`IDebugExpression2`介面，表示剖析準備要評估的運算式。  
  
 SDM 呼叫  [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)實際上評估運算式，並產生值。  
  
 中的實作`IDebugExpressionContext2::ParseText`，DE 使用 COM 的`CoCreateInstance`函式來具現化的運算式評估工具，並取得[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)介面 (請參閱中的範例`IDebugExpressionEvaluator`介面)。 然後呼叫 DE[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)取得[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)介面。 會使用這個介面的實作中`IDebugExpression2::EvaluateSync`和`IDebugExpression2::EvaluateAsync`執行評估。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)