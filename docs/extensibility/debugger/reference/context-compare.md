---
description: 指定比較兩個記憶體內容的準則。
title: CONTEXT_COMPARE |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70f4621eaad5e494684e6c227959e13566a22eba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170779"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
指定比較兩個記憶體內容的準則。

## <a name="syntax"></a>Syntax

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
在清單中找出與目標記憶體內容相等的第一個記憶體內容。

`CONTEXT_LESS_THAN`\
找出清單中小於目標記憶體內容的第一個記憶體內容。

`CONTEXT_GREATER_THAN`\
找出清單中大於目標記憶體內容的第一個記憶體內容。

`CONTEXT_LESS_THAN_OR_EQUAL`\
找出清單中小於或等於目標記憶體內容的第一個記憶體內容。

`CONTEXT_GREATER_THAN_OR_EQUAL`\
找出清單中大於或等於目標記憶體內容的第一個記憶體內容。

`CONTEXT_SAME_SCOPE`\
找出清單中與目標記憶體內容相同範圍中的第一個記憶體內容。

`CONTEXT_SAME_FUNCTION`\
找出清單中的第一個記憶體內容，此內容位於與目標記憶體範圍相同的函式中。

`CONTEXT_SAME_MODULE`\
在與目標記憶體內容相同的模組中，尋找清單中的第一個記憶體內容。

`CONTEXT_SAME_PROCESS`\
在清單中尋找第一個記憶體內容，此內容位於與目標記憶體內容相同的進程中。

## <a name="remarks"></a>備註
以引數形式傳遞至 [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) 方法。

這些值是用來尋找清單中符合指定之比較準則的第一個記憶體內容。 記憶體內容會提供記憶體內容清單，以透過方法進行比較 `IDebugMemoryContext2::Compare` 。 接著會傳回清單中的第一個記憶體內容，比較運算子 `true` 接著會傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
