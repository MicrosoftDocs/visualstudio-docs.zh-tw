---
title: BP_TYPE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 02550141fb1857214d5bfd80d5dd86969bec9fba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737783"
---
# <a name="bp_type"></a>BP_TYPE
指定斷點是位於代碼位置、資料位置還是其他類型的斷點。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>欄位
`BPT_NONE`\
指定無斷點類型。

`BPT_CODE`\
指定代碼斷點。

`BPT_DATA`\
指定數據斷點。

`BPT_SPECIAL`\
指定既不是代碼也不是數據類型的斷點。 此類型已棄用,不應使用。

## <a name="remarks"></a>備註
作為參數傳遞給[獲取斷點類型](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)和[獲取斷點類型](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)方法。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
