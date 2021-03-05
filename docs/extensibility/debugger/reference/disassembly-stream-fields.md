---
description: 指定要對反組解碼欄位取得哪些資訊。
title: DISASSEMBLY_STREAM_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_FIELDS
helpviewer_keywords:
- DISASSEMBLY_STREAM_FIELDS enumeration
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb45f492a58bd079a1b73212fc9473041d10589
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170467"
---
# <a name="disassembly_stream_fields"></a>DISASSEMBLY_STREAM_FIELDS
指定要對反組解碼欄位取得哪些資訊。

## <a name="syntax"></a>Syntax

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
初始化/使用 `bstrAddress` 欄位。

`DSF_ADDRESSOFFSET`\
初始化/使用 `bstrAddressOffset` 欄位。

`DSF_CODEBYTES`\
初始化/使用 `bstrCodeBytes` 欄位。

`DSF_OPCODE`\
初始化/使用 `bstrOpCode` 欄位。

`DSF_OPERANDS`\
初始化/使用 `bstrOperands` 欄位。

`DSF_SYMBOL`\
初始化/使用 `bstrSymbol` 欄位。

`DSF_CODELOCATIONID`\
初始化/使用 `uCodeLocationId` 欄位。

`DSF_POSITION`\
初始化/使用 `posBeg` 和 `posEnd` 欄位。

`DSF_DOCUMENTURL`\
初始化/使用 `bstrDocumentUrl` 欄位。

`DSF_BYTEOFFSET`\
初始化/使用 `dwByteOffset` 欄位。

`DSF_FLAGS`\
初始化/使用 `dwFlags` ([DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)) ] 欄位。

`DSF_OPERANDS_SYMBOLS`\
在欄位中包含符號名稱 `bstrOperands` 。

`DSF_ALL`\
指定反組解碼資料流程的所有欄位。

## <a name="remarks"></a>備註
以參數形式傳遞至 [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) 方法，以指出要初始化 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) 結構的哪些欄位。

用於結構的 `dwFields` 成員 `DisassemblyData` ，以指出傳回結構時使用的欄位和有效的欄位。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [讀取](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
