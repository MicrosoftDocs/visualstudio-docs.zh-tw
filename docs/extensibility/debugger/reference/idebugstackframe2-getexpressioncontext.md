---
title: "IDebugStackFrame2::GetExpressionContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetExpressionContext"
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

取得目前的內容中的運算式評估為堆疊框架和執行緒的評估內容。  
  
## 語法  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```c#  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### 參數  
 `ppExprCxt`  
 \[\] out傳回[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)表示運算式評估內容的物件。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 一般來說，運算式評估內容可以被視為執行運算式評估的範圍。  呼叫[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)方法進行剖析的運算式，並接著會呼叫所產生的[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)或[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)方法來評估剖析的運算式。  
  
## 請參閱  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)