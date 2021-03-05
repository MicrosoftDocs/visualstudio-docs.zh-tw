---
description: 列舉控制運算式評估之旗標的有效值。
title: EVALFLAGS90 |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2080eba4b8319045dcd4d3603d1e6441fafed97d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150922"
---
# <a name="evalflags90"></a>EVALFLAGS90
列舉控制運算式評估之旗標的有效值。 此列舉會擴充 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 列舉。

## <a name="syntax"></a>Syntax

```cpp
enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
typedef DWORD EVALFLAGS90;
```

```csharp
public enum enum_EVALFLAGS90
{
    // VS 8.0 values
    EVAL90_RETURNVALUE                 = 0x0002,
    EVAL90_NOSIDEEFFECTS               = 0x0004,
    EVAL90_ALLOWBPS                    = 0x0008,
    EVAL90_ALLOWERRORREPORT            = 0x0010,
    EVAL90_FUNCTION_AS_ADDRESS         = 0x0040,
    EVAL90_NOFUNCEVAL                  = 0x0080,
    EVAL90_NOEVENTS                    = 0x1000,
    EVAL90_DESIGN_TIME_EXPR_EVAL       = 0x2000,
    EVAL90_ALLOW_IMPLICIT_VARS         = 0x4000,

    // Values added in VS 9.0
    EVAL90_FORCE_EVALUATION_NOW        = 0x8000
};
```

## <a name="fields"></a>欄位
`EVAL90_RETURNVALUE`\
指定要評估的傳回值（如果有的話）。

`EVAL90_NOSIDEEFFECTS`\
指定不允許副作用。

`EVAL90_ALLOWBPS`\
指定在中斷點上停止。

`EVAL90_ALLOWERRORREPORT`\
指定要允許的主機錯誤報表。 主要用於 Internet Explorer 腳本中的運算式評估。

`EVAL90_FUNCTION_AS_ADDRESS`\
強制將函數評估為位址，而不是叫用函數。

`EVAL90_NOFUNCEVAL`\
防止評估函數。 例如，請考慮 `int` 運算式中的 token `myExpression(int) + 10` 。 此函數可以正確地評估為位址，但不能作為值。

`EVAL90_NOEVENTS`\
旗標，表示在運算式評估期間發生的事件，不應該傳送至會話 debug manager (SDM) 或 IDE。

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
啟用設計時程表達式評估。

`EVAL90_ALLOW_IMPLICIT_VARS`\
允許隱含變數建立。

`EVAL90_FORCE_EVALUATION_NOW`\
強制立即進行評估。 這在處理要求時很有用，例如使用者要求。

## <a name="requirements"></a>規格需求
標頭： Msdbg90。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
