---
title: CONTEXT_COMPARE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737612"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
指定比較兩個記憶體上下文的條件。

## <a name="syntax"></a>語法

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>欄位
`CONTEXT_EQUAL`\
在清單中尋找與目標記憶體上下文相等的第一個記憶體上下文。

`CONTEXT_LESS_THAN`\
查找清單中的第一個記憶體上下文,該上下文小於目標記憶體上下文。

`CONTEXT_GREATER_THAN`\
尋找清單中大於目標記憶體上下文的第一個記憶體上下文。

`CONTEXT_LESS_THAN_OR_EQUAL`\
尋找清單中小於或等於目標記憶體上下文的第一個記憶體上下文。

`CONTEXT_GREATER_THAN_OR_EQUAL`\
尋找清單中大於或等於目標記憶體上下文的第一個記憶體上下文。

`CONTEXT_SAME_SCOPE`\
尋找清單中與目標記憶體上下文位於同一作用域中的第一個記憶體上下文。

`CONTEXT_SAME_FUNCTION`\
尋找清單中與目標記憶體作用域具有相同函數的第一個記憶體上下文。

`CONTEXT_SAME_MODULE`\
尋找清單中與目標記憶體上下文位於同一模組中的第一個記憶體上下文。

`CONTEXT_SAME_PROCESS`\
尋找清單中與目標記憶體上下文處於相同進程的第一個記憶體上下文。

## <a name="remarks"></a>備註
作為參數傳遞給[比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)方法。

這些值用於查找清單中滿足指定比較條件的第一個記憶體上下文。 為記憶體上下文提供記憶體上下文的清單,以便通過方法`IDebugMemoryContext2::Compare`比較自身。 然後返回清單中的第一個記憶體上下文,`true`然後返回比較運算符。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
