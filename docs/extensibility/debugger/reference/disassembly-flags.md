---
title: DISASSEMBLY_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_FLAGS
helpviewer_keywords:
- DISASSEMBLY_FLAGS enumeration
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0160a14a4ad20e7144e48f767fad88951ca1e473
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318394"
---
# <a name="disassemblyflags"></a>DISASSEMBLY_FLAGS
指定反組譯碼的旗標。

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
指出這項指示是比前一個不同的文件中。

`DF_DISABLED`\
表示將不會執行這項指示。

`DF_INSTRUCTION_ACTIVE`\
指出這項指示是其中一個要執行的下一步 的指示 （可能會有多個）。

`DF_DATA`\
指出這項指示是真正的資料 （而不是程式碼）。

`DF_HASSOURCE`\
指出這個指示會有來源。 一些指示，例如程式碼剖析或記憶體回收集合程式碼，有沒有對應的來源。

`DF_DOCUMENT_CHECKSUM`\
表示`bstrDocumentUrl`欄位包含總和檢查碼資料，在文件 URL。 請參閱 < 備註 > 一節[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構總和檢查碼資料的儲存方式。

## <a name="remarks"></a>備註
做`dwFlags`隸屬[DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)結構。

這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
