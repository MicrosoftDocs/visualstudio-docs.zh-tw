---
title: BP_ERROR_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738074"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
指定斷點的錯誤類型。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>欄位
`BPET_NONE`\
指定無斷點錯誤。

`BPET_TYPE_WARNING`\
指定警告樣式斷點錯誤。

`BPET_TYPE_ERROR`\
指定錯誤樣式斷點錯誤。

`BPET_SEV_HIGH`\
指定高嚴重性斷點錯誤。

`BPET_SEV_GENERAL`\
指定中等嚴重性斷點錯誤。

`BPET_SEV_LOW`\
指定低嚴重性斷點錯誤。

`BPET_TYPE_MASK`\
指定遮罩式斷點錯誤。

`BPET_SEV_MASK`\
指定嚴重性蒙版樣式斷點錯誤。

`BPET_GENERAL_WARNING`\
指定常規警告樣式斷點錯誤。

`BPET_GENERAL_ERROR`\
指定一般錯誤樣式斷點錯誤。

`BPET_ALL`\
指定所有斷點錯誤類型。

## <a name="remarks"></a>備註
這些值可以與位組合,`OR`並`dwType`用於[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構的成員。 作為參數傳遞給[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)方法。

斷點錯誤類型由類型和嚴重性組成。 這意味著斷點錯誤類型本身不僅僅是一種類型(例如 ,,)`BPET_TYPE_ERROR`或嚴重性(例如`BPET_SEV_GENERAL`)。 `BPET_GENERAL_WARNING`並為`BPET_GENERAL_ERROR`常規警告和錯誤斷點提供預定義值。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
