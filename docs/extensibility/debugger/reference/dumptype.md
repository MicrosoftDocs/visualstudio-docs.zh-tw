---
title: DUMPTYPE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d4d42709efdefe097b4c8a78a0b00f45f2e1a2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737210"
---
# <a name="dumptype"></a>DUMPTYPE
指定程式的狀態 (（例如，執行中的執行緒、堆疊框架和目前的指令位址) 傾印）。

## <a name="syntax"></a>語法

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="fields"></a>欄位
`DUMP_MINIDUMP`\
指定小型的 compact 傾印。

`DUMP_FULLDUMP`\
指定大型的完整傾印。

## <a name="remarks"></a>備註
以引數形式傳遞至 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) 方法。

## <a name="requirements"></a>需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
