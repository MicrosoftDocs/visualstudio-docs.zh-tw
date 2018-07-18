---
title: EVALFLAGS |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c718414749bb6c748f25fb90837644fe984a274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101998"
---
# <a name="evalflags"></a>EVALFLAGS
指定控制運算式評估的旗標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_EVALFLAGS {  
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
  
```csharp  
public enum enum_EVALFLAGS {  
   EVAL_RETURNVALUE = 0x0002,  
   EVAL_NOSIDEEFFECTS = 0x0004,  
   EVAL_ALLOWBPS = 0x0008,  
   EVAL_ALLOWERRORREPORT = 0x0010,  
   EVAL_FUNCTION_AS_ADDRESS = 0x0040,  
   EVAL_NOFUNCEVAL = 0x0080,  
   EVAL_NOEVENTS = 0x1000  
}  
```  
  
## <a name="members"></a>成員  
 EVAL_RETURNVALUE  
 指定的評估傳回的值，如果有的話。  
  
 EVAL_NOSIDEEFFECTS  
 指定不允許副作用。  
  
 EVAL_ALLOWBPS  
 指定中斷點停止。  
  
 EVAL_ALLOWERRORREPORT  
 指定允許主應用程式報告的錯誤。 主要用於 Internet Explorer 中指令碼中的運算式評估。  
  
 EVAL_FUNCTION_AS_ADDRESS  
 要評估做為位址，而不是叫用函式的強制函式。  
  
 EVAL_NOFUNCEVAL  
 函式可防止在評估。 例如，請考慮`int`運算式中的語彙基元`myExpression(int) + 10`。 此函式可以正確評估，為位址，但不是能作為值。  
  
 EVAL_NOEVENTS  
 旗標，表示工作階段的偵錯管理員 (SDM) 或 IDE，您不應該傳送之運算式評估期間發生的事件。  
  
## <a name="remarks"></a>備註  
 這些旗標會傳遞做為引數[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)和[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法。  
  
 這些旗標可能會與位元 OR 運算結合。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)