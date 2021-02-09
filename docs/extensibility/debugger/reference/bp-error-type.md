---
title: BP_ERROR_TYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b67b28c61624b73787dabe9fd24c4c39ff9b3c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853048"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
指定中斷點的錯誤類型。

## <a name="syntax"></a>Syntax

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
指定無中斷點錯誤。

`BPET_TYPE_WARNING`\
指定警告樣式的中斷點錯誤。

`BPET_TYPE_ERROR`\
指定錯誤樣式的中斷點錯誤。

`BPET_SEV_HIGH`\
指定高嚴重性的中斷點錯誤。

`BPET_SEV_GENERAL`\
指定中嚴重性的中斷點錯誤。

`BPET_SEV_LOW`\
指定低嚴重性的中斷點錯誤。

`BPET_TYPE_MASK`\
指定遮罩樣式的中斷點錯誤。

`BPET_SEV_MASK`\
指定嚴重性遮罩樣式的中斷點錯誤。

`BPET_GENERAL_WARNING`\
指定一般警告樣式的中斷點錯誤。

`BPET_GENERAL_ERROR`\
指定一般錯誤樣式的中斷點錯誤。

`BPET_ALL`\
指定所有中斷點錯誤類型。

## <a name="remarks"></a>備註
這些值可能會與位結合 `OR` ，並用於 `dwType` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 結構的成員。 以參數形式傳遞至 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) 方法。

中斷點錯誤類型是由型別和嚴重性所組成。 這表示，中斷點錯誤類型絕不只是類型 (例如， `BPET_TYPE_ERROR` ) 或嚴重性 (例如， `BPET_SEV_GENERAL`) 本身。 `BPET_GENERAL_WARNING` 並 `BPET_GENERAL_ERROR` 為一般警告和錯誤中斷點提供預先定義的值。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
