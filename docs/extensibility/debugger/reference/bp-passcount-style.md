---
title: BP_PASSCOUNT_STYLE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737925"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
指定與斷點通過計數關聯的條件,這些條件會導致斷點觸發。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>欄位
`BP_PASSCOUNT_NONE`\
指定無斷點傳遞計數樣式。

`BP_PASSCOUNT_EQUAL`\
將斷點傳遞計數樣式設置為相等。 當斷點被擊中的次數等於通過計數時,斷點將觸發。

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
將斷點傳遞計數樣式設置為相等或更大。 當斷點命中的次數等於或大於通過計數時,斷點將觸發。

`BP_PASSCOUNT_MOD`\
指定蒙杜洛通數。 例如,如果傳遞計數是類型`BP_PASSCOUNT_MOD`,並且通過計數值為 4,則每次命中計數為 4 的倍數時,斷點都會觸發。

## <a name="remarks"></a>備註
用於BP_PASSCOUNT結構`stylePassCount`的成員,該[BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)結構依次是[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
