---
title: PARSEFLAGS |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714110"
---
# <a name="parseflags"></a>PARSEFLAGS
指定如何剖析運算式。

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
 指出運算式不是語句。

 `PARSE_FUNCTION_AS_ADDRESS`\
 指出將會剖析運算式 (，並在稍後將) 評估為位址。

 `PARSE_DESIGN_TIME_EXPR_EVAL`\
 指出運算式是在設計階段進行剖析 (也就是開啟設計工具) 。

## <a name="remarks"></a>備註
 以參數形式傳遞至 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) 和 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 方法。

## <a name="requirements"></a>需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [剖析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
