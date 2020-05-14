---
title: BP_UNBOUND_REASON |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737781"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
給出斷點未綁定的原因。

## <a name="syntax"></a>語法

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
已卸載包含斷點的代碼。

`BPUR_BREAKPOINT_REBIND`\
斷點已反彈到其他位置。 當斷點移動時,或者斷點綁定到具有不再有效的路徑的檔時,可以在"編輯並繼續"操作之後發生這種情況。

`BPUR_ BREAKPOINT_ERROR`\
斷點在綁定後被確定為錯誤。 這種情況不再有效的託管斷點會發生這種情況。

## <a name="remarks"></a>備註
由[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
