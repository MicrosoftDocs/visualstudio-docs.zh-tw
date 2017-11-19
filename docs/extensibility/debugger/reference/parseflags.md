---
title: "PARSEFLAGS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PARSEFLAGS
helpviewer_keywords: PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9c96eb60c397093fb5ec3291a0b02ee7cbd07e34
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="parseflags"></a>PARSEFLAGS
指定如何剖析的運算式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```csharp  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>成員  
 PARSE_EXPRESSION  
 表示運算式不是陳述式。  
  
 PARSE_FUNCTION_AS_ADDRESS  
 表示運算式剖析 （和更新版本評估） 位址。  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 表示在設計階段期間剖析運算式 （也就是當設計工具開啟時）。  
  
## <a name="remarks"></a>備註  
 做為參數來傳遞[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)和[剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)方法。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)