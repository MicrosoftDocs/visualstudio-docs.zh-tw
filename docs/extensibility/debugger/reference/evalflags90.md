---
title: EVALFLAGS90 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- EVALFLAGS90 enumeration
ms.assetid: 64fb0139-8b04-4726-b52c-db2e04d65498
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01951885541ba4acce33f3e4f06f7106116ccc62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737097"
---
# <a name="evalflags90"></a>EVALFLAGS90
枚舉控制運算式計算的標誌的有效值。 此枚舉擴展了[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉。

## <a name="syntax"></a>語法

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
指定計算返回值(如果有)。

`EVAL90_NOSIDEEFFECTS`\
指定不允許副作用。

`EVAL90_ALLOWBPS`\
指定在斷點停止。

`EVAL90_ALLOWERRORREPORT`\
指定允許向主機報告的錯誤。 主要用於在 Internet 資源管理器中文本中的運算式計算。

`EVAL90_FUNCTION_AS_ADDRESS`\
強制函數作為位址計算,而不是調用函數。

`EVAL90_NOFUNCEVAL`\
防止計算函數。 例如,`int`考慮表達`myExpression(int) + 10`式 中的標記。 此功能可以正確計算為位址,但不能作為值。

`EVAL90_NOEVENTS`\
標記以指示不應將表達式計算期間發生的事件發送到工作階段調試管理器 (SDM) 或 IDE。

`EVAL90_DESIGN_TIME_EXPR_EVAL`\
啟用設計時表達式計算。

`EVAL90_ALLOW_IMPLICIT_VARS`\
允許隱式變數創建。

`EVAL90_FORCE_EVALUATION_NOW`\
強制立即進行評估。 這在服務請求(如使用者請求)時非常有用。

## <a name="requirements"></a>需求
標題: Msdbg90.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
