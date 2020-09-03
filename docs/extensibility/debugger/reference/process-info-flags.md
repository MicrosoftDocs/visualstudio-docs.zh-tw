---
title: PROCESS_INFO_FLAGS |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
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
表示進程是系統進程。

`PIFLAG_DEBUGGER_ATTACHED`\
表示進程正在由偵錯工具進行調試。 它可能是 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 偵錯工具，也可能是一些其他偵錯工具，例如 WinDbg。

`PIFLAG_PROCESS_STOPPED`\
表示進程已停止。 只有 `PIFLAG_DEBUGGER_ATTACHED` 在同時指定時才有效。 可在 Visual Studio 2005 和更新版本中使用。

`PIFLAG_PROCESS_RUNNING`\
表示進程正在執行中。 只有 `PIFLAG_DEBUGGER_ATTACHED` 在同時指定時才有效。 可在 Visual Studio 2005 和更新版本中使用。

## <a name="remarks"></a>備註

用於 `Flags` [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 結構的成員。

這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>需求

標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
