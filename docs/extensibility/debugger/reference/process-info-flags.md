---
title: PROCESS_INFO_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713956"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

描述或指定進程的屬性。

## <a name="syntax"></a>語法

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>欄位

`PIFLAG_SYSTEM_PROCESS`\
指示該過程是系統進程。

`PIFLAG_DEBUGGER_ATTACHED`\
指示調試器正在調試進程。 它可能是調試[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]器,或者可能是其他調試器,例如 WinDbg。

`PIFLAG_PROCESS_STOPPED`\
指示進程已停止。 僅在也指定`PIFLAG_DEBUGGER_ATTACHED`時有效。 可在 Visual Studio 2005 及更高版本提供。

`PIFLAG_PROCESS_RUNNING`\
指示進程正在運行。 僅在也指定`PIFLAG_DEBUGGER_ATTACHED`時有效。 可在 Visual Studio 2005 及更高版本提供。

## <a name="remarks"></a>備註

用於[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)結構`Flags`的成員。

這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求

標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱

- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
