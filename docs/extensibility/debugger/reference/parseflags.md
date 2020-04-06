---
title: PARSEFLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0cc70fdd9fe1279e4d419a422b970eb3d3b07c65
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714110"
---
# <a name="parseflags"></a>PARSEFLAGS
指定如何解析表達式。

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

## <a name="fields"></a>欄位
 `PARSE_EXPRESSION`\
 指示表達式不是語句。

 `PARSE_FUNCTION_AS_ADDRESS`\
 指示表達式將作為位址進行解析(和以後計算)。

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 指示在設計期間(即設計器打開時)正在分析表達式。

## <a name="remarks"></a>備註
 為參數傳遞給[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)與[Parse 方法](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
