---
title: PARSEFLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da6b3641a33a19cef01f9a6a4a9a833643169f25
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006563"
---
# <a name="parseflags"></a>PARSEFLAGS
指定如何剖析的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>成員  
 PARSE_EXPRESSION  
 表示運算式不是陳述式。  
  
 PARSE_FUNCTION_AS_ADDRESS  
 表示運算式的剖析 （並稍後再評估） 位址。  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 表示在設計階段剖析運算式 （也就是當設計工具開啟時）。  
  
## <a name="remarks"></a>備註  
 做為參數傳遞[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)並[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間:Microsoft.VisualStudio.Debugger.Interop  
  
 組件︰Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)