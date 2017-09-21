---
title: "EVALFLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVALFLAGS"
helpviewer_keywords: 
  - "EVALFLAGS 列舉型別"
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# EVALFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定控制運算式評估的旗標。  
  
## 語法  
  
```cpp#  
enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
};  
typedef DWORD EVALFLAGS;  
```  
  
```c#  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## Members  
 EVAL\_RETURNVALUE  
 指定傳回的值，如果有的話，進行評估。  
  
 EVAL\_NOSIDEEFFECTS  
 指定不允許副作用。  
  
 EVAL\_ALLOWBPS  
 指定中斷點停止。  
  
 EVAL\_ALLOWERRORREPORT  
 指定錯誤報告給主應用程式，以允許。  主要用於在 Internet Explorer 中的指令碼中運算式的評估。  
  
 EVAL\_FUNCTION\_AS\_ADDRESS  
 要評估的地址，而不是叫用函式的部隊函式。  
  
 EVAL\_NOFUNCEVAL  
 函式會防止進行評估。  例如，假設`int`運算式中的語彙基元`myExpression(int) + 10`。  為地址，但不是以一個值，就可以正確地評估此函式。  
  
 EVAL\_NOEVENTS  
 旗標，表示 \[工作階段偵錯管理員 \(SDM\) 或 IDE，您不應該傳送運算式的評估期間發生的事件。  
  
## 備註  
 這些旗標會當做引數傳遞[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)和[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法。  
  
 可能與位元的 OR 合併使用這些旗標。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)