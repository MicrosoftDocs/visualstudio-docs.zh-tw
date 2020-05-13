---
title: DISASSEMBLY_STREAM_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d10f2143cbefa86442e4087ac098020f5f2bd6ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737362"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
指定要檢索的有關拆解欄位的資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
typedef DWORD DISASSEMBLY_STREAM_FIELDS;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_FIELDS {
    DSF_ADDRESS          = 0x00000001,
    DSF_ADDRESSOFFSET    = 0x00000002,
    DSF_CODEBYTES        = 0x00000004,
    DSF_OPCODE           = 0x00000008,
    DSF_OPERANDS         = 0x00000010,
    DSF_SYMBOL           = 0x00000020,
    DSF_CODELOCATIONID   = 0x00000040,
    DSF_POSITION         = 0x00000080,
    DSF_DOCUMENTURL      = 0x00000100,
    DSF_BYTEOFFSET       = 0x00000200,
    DSF_FLAGS            = 0x00000400,
    DSF_OPERANDS_SYMBOLS = 0x00010000,
    DSF_ALL              = 0x000107ff
};
```

## <a name="fields"></a>欄位
`DSF_ADDRESS`\
初始化/使用`bstrAddress`欄位。

`DSF_ADDRESSOFFSET`\
初始化/使用`bstrAddressOffset`欄位。

`DSF_CODEBYTES`\
初始化/使用`bstrCodeBytes`欄位。

`DSF_OPCODE`\
初始化/使用`bstrOpCode`欄位。

`DSF_OPERANDS`\
初始化/使用`bstrOperands`欄位。

`DSF_SYMBOL`\
初始化/使用`bstrSymbol`欄位。

`DSF_CODELOCATIONID`\
初始化/使用`uCodeLocationId`欄位。

`DSF_POSITION`\
初始化/使用`posBeg`和`posEnd`欄位。

`DSF_DOCUMENTURL`\
初始化/使用`bstrDocumentUrl`欄位。

`DSF_BYTEOFFSET`\
初始化/使用`dwByteOffset`欄位。

`DSF_FLAGS`\
初始化/使用`dwFlags`([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) 欄位。

`DSF_OPERANDS_SYMBOLS`\
在`bstrOperands`欄位中包括符號名稱。

`DSF_ALL`\
指定拆解流的所有欄位。

## <a name="remarks"></a>備註
作為參數傳遞給[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)方法,以指示要初始化[拆解數據](../../../extensibility/debugger/reference/disassemblydata.md)結構的哪些欄位。

用於`dwFields``DisassemblyData`結構的成員,用於指示在返回結構時使用哪些欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [讀](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
