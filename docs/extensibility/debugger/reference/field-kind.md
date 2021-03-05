---
description: 指定 IDebugField 物件中所含的欄位種類。
title: FIELD_KIND |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 519b18f9e4b0329ded9b17ec0152f36e37377df0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150857"
---
# <a name="field_kind"></a>FIELD_KIND
指定 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件中所含的欄位種類。

## <a name="syntax"></a>Syntax

```cpp
enum enum_FIELD_KIND {
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
    FIELD_SYM_MEMBER      = 0x01000000,
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
    FIELD_SYM_MEMBER      = 0x01000000,
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
表示欄位只是型別。

`FIELD_KIND_SYMBOL`\
表示欄位是符號，其類型、名稱和其他資訊。

`FIELD_TYPE_PRIMITIVE`\
表示欄位是基本資料類型。

`FIELD_TYPE_STRUCT`\
表示欄位為結構。

`FIELD_TYPE_CLASS`\
表示欄位為類別。

`FIELD_TYPE_INTERFACE`\
表示欄位為介面。

`FIELD_TYPE_UNION`\
表示欄位為聯集。

`FIELD_TYPE_ARRAY`\
表示欄位為數組。

`FIELD_TYPE_METHOD`\
表示欄位是方法。

`FIELD_TYPE_BLOCK`\
表示此欄位為區塊。

`FIELD_TYPE_POINTER`\
表示欄位是指標。

`FIELD_TYPE_ENUM`\
表示欄位是列舉資料類型。

`FIELD_TYPE_LABEL`\
表示欄位是標籤。

`FIELD_TYPE_TYPEDEF`\
表示此欄位為 typedef。

`FIELD_TYPE_BITFIELD`\
表示欄位是位位。

`FIELD_TYPE_NAMESPACE`\
表示此欄位為命名空間。

`FIELD_TYPE_MODULE`\
表示欄位為模組。

`FIELD_TYPE_DYNAMIC`\
表示欄位為動態。

`FIELD_TYPE_PROP`\
表示欄位是屬性。

`FIELD_TYPE_INNERCLASS`\
表示欄位是內部類別。

`FIELD_TYPE_REFERENCE`\
表示欄位為參考。

`FIELD_TYPE_EXTENDED`\
保留供未來使用。

`FIELD_SYM_MEMBER`\
表示欄位是成員。

`FIELD_SYM_LOCAL`\
表示欄位為本機。

`FIELD_SYM_PARAMETER`\
表示欄位是參數。

`FIELD_SYM_THIS`\
表示此欄位為 "this" 指標。

`FIELD_SYM_GLOBAL`\
表示此欄位為 global。

`FIELD_SYM_PROP_GETTER`\
表示欄位會抓取屬性。

`FIELD_SYM_PROP_SETTER`\
表示欄位會設定屬性。

`FIELD_SYM_EXTENDED`\
保留供未來使用。

`FIELD_KIND_MASK`\
表示欄位種類的遮罩。

`FIELD_TYPE_MASK`\
表示欄位類型的遮罩。

`FIELD_SYM_MASK`\
表示符號資訊的遮罩。

## <a name="remarks"></a>備註
從對 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 方法的呼叫傳回。

根據欄位類型，可以在[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面上呼叫[QueryInterface](/cpp/atl/queryinterface) ，以取得更明確的介面形式。 例如，如果 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 傳回 `FIELD_TYPE_METHOD` ，您就可以呼叫 `QueryInterface` I `DebugField` 來取得 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 介面。

## <a name="requirements"></a>規格需求
標頭： sh. h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
