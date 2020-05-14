---
title: DOCCONTEXT_COMPARE |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737224"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
指定比較兩個文檔上下文的條件。

## <a name="syntax"></a>語法

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>欄位
`DOCCONTEXT_EQUAL`\
尋找清單中與目標文件上下文相等的第一個文檔上下文。

`DOCCONTEXT_LESS_THAN`\
尋找清單中的第一個小於目標文件上下文的文件上下文。

`DOCCONTEXT_GREATER_THAN`\
尋找清單中大於目標文件上下文的第一個文檔上下文。

`DOCCONTEXT_SAME_DOCUMENT`\
尋找清單中與目標文件上下文位於同一文檔中的第一個文件上下文。

## <a name="remarks"></a>備註
作為參數傳遞給[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)方法。

這些值用於指定查找清單中的第一個文檔上下文的比較條件。 文檔上下文將給出文檔上下文的清單,以便`IDebugDocumentContext2::Compare`通過方法 比較自身。 然後傳回清單中的第一個文件上下文`true`, 然後傳回比較運算符。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
