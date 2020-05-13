---
title: 埃瓦爾格茲 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EVALFLAGS
helpviewer_keywords:
- EVALFLAGS enumeration
ms.assetid: 7b2cb14a-511a-4fef-9e4f-308139719fba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4136726e5c8b798121dbd38975d8f2bb935ed04a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737117"
---
# <a name="evalflags"></a>EVALFLAGS
指定控制表達式計算的標誌。

## <a name="syntax"></a>語法

```cpp
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

```csharp
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

## <a name="fields"></a>欄位
`EVAL_RETURNVALUE`\
指定計算返回值(如果有)。

`EVAL_NOSIDEEFFECTS`\
指定不允許副作用。

`EVAL_ALLOWBPS`\
指定在斷點停止。

`EVAL_ALLOWERRORREPORT`\
指定允許向主機報告錯誤。 主要用於在 Internet 資源管理器中文本中的運算式計算。

`EVAL_FUNCTION_AS_ADDRESS`\
強制函數作為位址計算,而不是調用函數。

`EVAL_NOFUNCEVAL`\
防止計算函數。 例如,`int`考慮表達`myExpression(int) + 10`式 中的標記。 此功能可以正確計算為位址,但不能作為值。

`EVAL_NOEVENTS`\
標記以指示不應將表達式計算期間發生的事件發送到工作階段調試管理器 (SDM) 或 IDE。

## <a name="remarks"></a>備註
這些標誌作為參數傳遞給[評估Async](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)和[評估同步](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)方法。

這些標誌可以與位或組合。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
