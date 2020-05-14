---
title: DISASSEMBLY_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba6d9db3ad2cb1f9bbc9e3cea27aba939c6dd499
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737367"
---
# <a name="disassembly_flags"></a>DISASSEMBLY_FLAGS
指定拆卸的標誌。

## <a name="syntax"></a>語法

```cpp
enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
typedef DWORD DISASSEMBLY_FLAGS;
```

```csharp
public enum enum_DISASSEMBLY_FLAGS {
    DF_DOCUMENTCHANGE     = 0x00000001,
    DF_DISABLED           = 0x00000002,
    DF_INSTRUCTION_ACTIVE = 0x00000004,
    DF_DATA               = 0x00000008,
    DF_HASSOURCE          = 0x00000010,
    DF_DOCUMENT_CHECKSUM  = 0x00000020
};
```

## <a name="fields"></a>欄位
`DF_DOCUMENTCHANGE`\
指示此指令位於與前一個不同的文檔中。

`DF_DISABLED`\
指示此指令不會執行。

`DF_INSTRUCTION_ACTIVE`\
指示此指令是要執行的下一個指令之一(可能有多個指令)。

`DF_DATA`\
指示此指令實際上是數據(不是代碼)。

`DF_HASSOURCE`\
指示此指令具有源。 某些說明(如分析代碼或垃圾回收代碼)沒有相應的源。

`DF_DOCUMENT_CHECKSUM`\
指示`bstrDocumentUrl`欄位包含文件 URL 之後的校驗和數據。 有關如何存儲校驗和數據的,請參閱["拆解資料](../../../extensibility/debugger/reference/disassemblydata.md)結構的備註"部分。

## <a name="remarks"></a>備註
用作`dwFlags`[拆解數據](../../../extensibility/debugger/reference/disassemblydata.md)結構的成員。

這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
