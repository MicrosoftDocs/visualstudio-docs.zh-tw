---
description: 提供中斷點未系結的原因。
title: BP_UNBOUND_REASON |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13f723c6395b8b271d6f097d811c5a31569c5853
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067695"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
提供中斷點未系結的原因。

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="fields"></a>欄位
`BPUR_UNKNOWN`\
原因不明。

`BPUR_CODE_UNLOADED`\
包含中斷點的程式碼已經卸載。

`BPUR_BREAKPOINT_REBIND`\
中斷點已重新綁定至不同的位置。 當中斷點移動時，或當中斷點系結至路徑不再有效的檔案時，就會發生這種情況。

`BPUR_ BREAKPOINT_ERROR`\
中斷點會在系結之後判斷為錯誤。 這會發生在其條件不再有效的 managed 中斷點上。

## <a name="remarks"></a>備註
由 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) 方法傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
