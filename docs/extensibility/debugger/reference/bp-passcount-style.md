---
title: BP_PASSCOUNT_STYLE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0148a92ee37a4f9885c9c12a5076ff966051d20b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902110"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
指定與引發中斷點之中斷點傳遞計數相關聯的條件。

## <a name="syntax"></a>Syntax

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
指定無中斷點傳遞計數樣式。

`BP_PASSCOUNT_EQUAL`\
將中斷點傳遞計數樣式設定為相等。 中斷點叫用的次數等於傳遞計數時，就會引發中斷點。

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
將 [中斷點傳遞計數] 樣式設定為 [等於] 或 [大於]。 當中斷點的點擊次數等於或大於傳遞計數時，就會引發中斷點。

`BP_PASSCOUNT_MOD`\
指定模數傳遞計數。 例如，如果傳遞計數是型別 `BP_PASSCOUNT_MOD` ，而 pass count 值是4，則每次叫用計數為4的倍數時，就會引發中斷點。

## <a name="remarks"></a>備註
用於 `stylePassCount` [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 結構的成員，而該成員接著是 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 和 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 結構的成員。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
