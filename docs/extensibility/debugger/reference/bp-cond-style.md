---
description: 指定暫止和系結中斷點的中斷點條件樣式。
title: BP_COND_STYLE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c23549d1553902c00048f946d2711c497fbe2322
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144477"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
指定暫止和系結中斷點的中斷點條件樣式。

## <a name="syntax"></a>Syntax

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>欄位
`BP_COND_NONE`\
到達中斷點的位置時引發中斷點。 未指定中斷點條件。

`BP_COND_WHEN_TRUE`\
只有當與中斷點相關聯的條件運算式評估為時，才會引發中斷點 `true` 。

`BP_COND_WHEN_CHANGED`\
只有當與中斷點相關聯之條件運算式的值已從其先前的評估變更時，才會引發中斷點。

## <a name="remarks"></a>備註
用於 `styleCondition` [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) 結構的成員。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
