---
description: 指定控制運算式評估的旗標。
title: EVALFLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5bcf68b95bb905d41aaab906603cd4dd248e52ad
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095936"
---
# <a name="evalflags"></a>EVALFLAGS
指定控制運算式評估的旗標。

## <a name="syntax"></a>Syntax

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

## <a name="fields"></a>欄位
`EVAL_RETURNVALUE`\
指定要評估的傳回值（如果有的話）。

`EVAL_NOSIDEEFFECTS`\
指定不允許副作用。

`EVAL_ALLOWBPS`\
指定在中斷點上停止。

`EVAL_ALLOWERRORREPORT`\
指定要允許的主機錯誤報表。 主要用於 Internet Explorer 中腳本的運算式評估。

`EVAL_FUNCTION_AS_ADDRESS`\
強制將函數評估為位址，而不是叫用函數。

`EVAL_NOFUNCEVAL`\
防止評估函數。 例如，請考慮 `int` 運算式中的 token `myExpression(int) + 10` 。 此函數可以正確地評估為位址，但不能作為值。

`EVAL_NOEVENTS`\
旗標，表示在運算式評估期間發生的事件，不應該傳送至會話 debug manager (SDM) 或 IDE。

## <a name="remarks"></a>備註
這些旗標會以引數的形式傳遞至 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) 和 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) 方法。

這些旗標可以結合位 OR。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
