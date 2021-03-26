---
description: 指定要針對 debug 參考物件取得哪些資訊。
title: DEBUGREF_INFO_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 913490588fcf739e9659318cb72a9ca74d6db99d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096222"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
指定要針對 debug 參考物件取得哪些資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>欄位
`DEBUGREF_INFO_NAME`\
初始化/使用 `bstrName` 結構中的欄位。

`DEBUGREF_INFO_TYPE`\
初始化/使用 `bstrType` 結構中的欄位。

`DEBUGREF_INFO_VALUE`\
初始化/使用 `bstrValue` 結構中的欄位。

`DEBUGREF_INFO_ATTRIB`\
初始化/使用 `dwAttrib` 結構中的欄位。

`DEBUGREF_INFO_REFTYPE`\
初始化/使用 `dwRefType` 結構中的欄位。

`DEBUGREF_INFO_REF`\
初始化/使用 `pReference` 結構中的欄位。

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
值欄位應該包含此類型物件的自動展開值（如果有的話）。

`DEBUGREF_INFO_NONE`\
指出未設定任何旗標。

`DEBUGREF_INFO_ALL`\
指出旗標的遮罩。

## <a name="remarks"></a>備註
這些旗標會傳遞至 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) 和 [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) 方法，以指出要初始化 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 結構的哪些欄位。

用於結構的 `dwFields` 成員 `DEBUG_REFERENCE_INFO` ，以指出傳回結構時使用的欄位和有效的欄位。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
