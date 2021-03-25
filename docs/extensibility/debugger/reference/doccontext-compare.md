---
description: 指定用於比較兩個檔內容的準則。
title: DOCCONTEXT_COMPARE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096001"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
指定用於比較兩個檔內容的準則。

## <a name="syntax"></a>Syntax

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
在清單中尋找與目的檔案內容相等的第一個檔內容。

`DOCCONTEXT_LESS_THAN`\
在清單中尋找小於目的檔案內容的第一個檔內容。

`DOCCONTEXT_GREATER_THAN`\
在清單中尋找大於目的檔案內容的第一個檔內容。

`DOCCONTEXT_SAME_DOCUMENT`\
在與目的檔案內容相同的檔中，尋找清單中的第一個檔內容。

## <a name="remarks"></a>備註
以引數形式傳遞至 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) 方法。

這些值用來指定在清單中尋找第一個檔內容的比較準則。 檔內容會取得一份檔內容清單，以透過方法進行比較 `IDebugDocumentContext2::Compare` 。 接著會傳回清單中的第一個檔內容，其比較運算子會 `true` 傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
