---
title: FIELD_KIND |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cafe4a34745f3b34070f7d8fed1a246c806375a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736869"
---
# <a name="field_kind"></a>FIELD_KIND
指定[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件中包含的欄位類型。

## <a name="syntax"></a>語法

```cpp
enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
typedef DWORD FIELD_KIND;
```

```csharp
public enum enum_FIELD_KIND {
    FIELD_KIND_NONE       = 0x00000000,

    // Type of field
    FIELD_KIND_TYPE       = 0x00000001,
    FIELD_KIND_SYMBOL     = 0x00000002,

    // Storage type of the field
    FIELD_TYPE_PRIMITIVE  = 0x00000010,
    FIELD_TYPE_STRUCT     = 0x00000020,
    FIELD_TYPE_CLASS      = 0x00000040,
    FIELD_TYPE_INTERFACE  = 0x00000080,
    FIELD_TYPE_UNION      = 0x00000100,
    FIELD_TYPE_ARRAY      = 0x00000200,
    FIELD_TYPE_METHOD     = 0x00000400,
    FIELD_TYPE_BLOCK      = 0x00000800,
    FIELD_TYPE_POINTER    = 0x00001000,
    FIELD_TYPE_ENUM       = 0x00002000,
    FIELD_TYPE_LABEL      = 0x00004000,
    FIELD_TYPE_TYPEDEF    = 0x00008000,
    FIELD_TYPE_BITFIELD   = 0x00010000,
    FIELD_TYPE_NAMESPACE  = 0x00020000,
    FIELD_TYPE_MODULE     = 0x00040000,
    FIELD_TYPE_DYNAMIC    = 0x00080000,
    FIELD_TYPE_PROP       = 0x00100000,
    FIELD_TYPE_INNERCLASS = 0x00200000,
    FIELD_TYPE_REFERENCE  = 0x00400000,
    FIELD_TYPE_EXTENDED   = 0x00800000,

    // Specific information about symbols
    FIELD_SYM_MEMBER      = 0x01000000,
    FIELD_SYM_LOCAL       = 0x02000000,
    FIELD_SYM_PARAM       = 0x04000000,
    FIELD_SYM_THIS        = 0x08000000,
    FIELD_SYM_GLOBAL      = 0x10000000,
    FIELD_SYM_PROP_GETTER = 0x20000000,
    FIELD_SYM_PROP_SETTER = 0x40000000,
    FIELD_SYM_EXTENDED    = 0x80000000,

    FIELD_KIND_MASK       = 0x0000000f,
    FIELD_TYPE_MASK       = 0x00fffff0,
    FIELD_SYM_MASK        = 0xff000000,

    FIELD_KIND_ALL        = 0xffffffff
};
```

## <a name="fields"></a>欄位
`FIELD_KIND_TYPE`\
指示該欄位僅為類型。

`FIELD_KIND_SYMBOL`\
指示該欄位是符號,具有類型、名稱和其他資訊。

`FIELD_TYPE_PRIMITIVE`\
指示該欄位是基元數據類型。

`FIELD_TYPE_STRUCT`\
指示該欄位是一個結構。

`FIELD_TYPE_CLASS`\
指示該欄位是類。

`FIELD_TYPE_INTERFACE`\
指示該欄位是介面。

`FIELD_TYPE_UNION`\
指示該欄位是聯合。

`FIELD_TYPE_ARRAY`\
指示該欄位是陣組。

`FIELD_TYPE_METHOD`\
指示該欄位是一個方法。

`FIELD_TYPE_BLOCK`\
指示該欄位是塊。

`FIELD_TYPE_POINTER`\
指示該字段是指針。

`FIELD_TYPE_ENUM`\
指示該欄位是枚舉數據類型。

`FIELD_TYPE_LABEL`\
指示該欄位是一個標籤。

`FIELD_TYPE_TYPEDEF`\
指示該欄位是 typedef。

`FIELD_TYPE_BITFIELD`\
指示該欄位是位欄位。

`FIELD_TYPE_NAMESPACE`\
指示該欄位是命名空間。

`FIELD_TYPE_MODULE`\
指示該欄位是模組。

`FIELD_TYPE_DYNAMIC`\
指示該欄位是動態的。

`FIELD_TYPE_PROP`\
指示該欄位是屬性。

`FIELD_TYPE_INNERCLASS`\
指示該欄位是內部類。

`FIELD_TYPE_REFERENCE`\
指示該欄位是引用。

`FIELD_TYPE_EXTENDED`\
保留供未來使用。

`FIELD_SYM_MEMBER`\
指示該欄位是成員。

`FIELD_SYM_LOCAL`\
指示該欄位是本地的。

`FIELD_SYM_PARAMETER`\
指示該欄位是參數。

`FIELD_SYM_THIS`\
指示該欄位是「此」指標。

`FIELD_SYM_GLOBAL`\
指示該欄位是全域的。

`FIELD_SYM_PROP_GETTER`\
指示該欄位檢索屬性。

`FIELD_SYM_PROP_SETTER`\
指示該欄位設置屬性。

`FIELD_SYM_EXTENDED`\
保留供未來使用。

`FIELD_KIND_MASK`\
指示欄位類型的掩碼。

`FIELD_TYPE_MASK`\
指示欄位類型的掩碼。

`FIELD_SYM_MASK`\
指示符號資訊的蒙版。

## <a name="remarks"></a>備註
從調用[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)方法返回。

根據欄位的種類,可以在[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面上調用[查詢介面](/cpp/atl/queryinterface),以進行更具體的介面形式。 例如,如果[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_METHOD`返回,則可以`QueryInterface`調`DebugField`用 我 以獲取[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)介面。

## <a name="requirements"></a>需求
標題: sh.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
