---
title: FIELD_MODIFIERS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5589b1535fbe22f0b0c1f2f9c9e34f70a4e7e861
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874318"
---
# <a name="field_modifiers"></a>FIELD_MODIFIERS
指定欄位類型的修飾詞。

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
typedef DWORD FIELD_MODIFIERS;
```

```csharp
public enum enum_FIELD_MODIFIERS {
    FIELD_MOD_NONE             = 0x00000000,

    // Modifier of the field
    FIELD_MOD_ACCESS_NONE      = 0x00000001,
    FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,
    FIELD_MOD_ACCESS_PROTECTED = 0x00000004,
    FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,

    // Storage modifier of the field
    FIELD_MOD_NOMODIFIERS      = 0x00000010,
    FIELD_MOD_STATIC           = 0x00000020,
    FIELD_MOD_CONSTANT         = 0x00000040,
    FIELD_MOD_TRANSIENT        = 0x00000080,
    FIELD_MOD_VOLATILE         = 0x00000100,
    FIELD_MOD_ABSTRACT         = 0x00000200,
    FIELD_MOD_NATIVE           = 0x00000400,
    FIELD_MOD_SYNCHRONIZED     = 0x00000800,
    FIELD_MOD_VIRTUAL          = 0x00001000,
    FIELD_MOD_INTERFACE        = 0x00002000,
    FIELD_MOD_FINAL            = 0x00004000,
    FIELD_MOD_SENTINEL         = 0x00008000,
    FIELD_MOD_INNERCLASS       = 0x00010000,
    FIELD_TYPE_OPTIONAL        = 0x00020000,
    FIELD_MOD_BYREF            = 0x00040000,
    FIELD_MOD_HIDDEN           = 0x00080000,
    FIELD_MOD_MARSHALASOBJECT  = 0x00100000,
    FIELD_MOD_SPECIAL_NAME     = 0x00200000,
    FIELD_MOD_HIDEBYSIG        = 0x00400000,

    FIELD_MOD_WRITEONLY        = 0x80000000,
    FIELD_MOD_ACCESS_MASK      = 0x000000ff,
    FIELD_MOD_MASK             = 0xffffff00,
    FIELD_MOD_ALL              = 0x7fffffff
};
```

## <a name="fields"></a>欄位
`FIELD_MOD_ACCESS_TYPE`\
指出無法存取欄位。

`FIELD_MOD_ACCESS_PUBLIC`\
表示欄位具有公用存取權。

`FIELD_MOD_ACCESS_PROTECTED`\
表示欄位具有受保護的存取權。

`FIELD_MOD_ACCESS_PRIVATE`\
表示欄位具有私用存取。

`FIELD_MOD_NOMODIFIERS`\
表示欄位沒有修飾詞。

`FIELD_MOD_STATIC`\
表示欄位為靜態。

`FIELD_MOD_CONSTANT`\
表示欄位是常數。

`FIELD_MOD_TRANSIENT`\
表示欄位是暫時性的。

`FIELD_MOD_VOLATILE`\
表示欄位為 volatile。

`FIELD_MOD_ABSTRACT`\
表示欄位是抽象的。

`FIELD_MOD_NATIVE`\
表示此欄位為原生。

`FIELD_MOD_SYNCHRONIZED`\
表示欄位已同步處理。

`FIELD_MOD_VIRTUAL`\
表示欄位為虛擬。

`FIELD_MOD_INTERFACE`\
表示欄位為介面。

`FIELD_MOD_FINAL`\
表示欄位為 final。

`FIELD_MOD_SENTINEL`\
表示欄位是 sentinel。

`FIELD_MOD_INNERCLASS`\
表示欄位是內部類別。

`FIELD_TYPE_OPTIONAL`\
表示欄位是選擇性的。

`FIELD_MOD_BYREF`\
表示此欄位為參考引數。 這特別適用于方法引數。

`FIELD_MOD_HIDDEN`\
表示欄位必須隱藏或顯示在另一個內容中;例如， [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 靜態區域變數。

`FIELD_MOD_MARSHALASOBJECT`\
表示欄位代表具有介面的物件 `IUnknown` 。

`FIELD_MOD_SPECIAL_NAME`\
表示欄位具有特殊名稱，例如， `.ctor` 僅 () 的函式 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 。

`FIELD_MOD_HIDEBYSIG`\
表示欄位已套用 `Overloads` 關鍵字 ([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] 僅) 。

`FIELD_MOD_WRITEONLY`\
表示欄位為僅限寫入。 此值不包含在中 `FIELD_MOD_ALL` ，因為這類僅限寫入欄位的用途僅供函數評估之用。 使用者必須明確要求 `FIELD_MOD_WRITEONLY` 欄位。

`FIELD_MOD_ACCESS_MASK`\
表示欄位存取的遮罩。

`FIELD_MOD_MASK`\
表示欄位修飾詞的遮罩。

## <a name="remarks"></a>備註
用於 `dwModifiers` [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 結構的成員。

這些值也會傳遞至 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) 方法，以篩選特定欄位。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
