---
title: PROCESS_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55157ab9a045b404175369e9682c525929f5e624
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460833"
---
# <a name="processinfoflags"></a>PROCESS_INFO_FLAGS

描述或指定的處理程序的屬性。

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
表示處理程序是系統處理序。

`PIFLAG_DEBUGGER_ATTACHED`\
表示處理程序正在偵錯的偵錯工具。 它可能是[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具，或它可能是某些其他偵錯工具，例如 WinDbg。

`PIFLAG_PROCESS_STOPPED`\
表示處理程序已停止。 才有效`PIFLAG_DEBUGGER_ATTACHED`同時指定。 適用於 Visual Studio 2005 和更新版本。

`PIFLAG_PROCESS_RUNNING`\
表示處理序正在執行。 才有效`PIFLAG_DEBUGGER_ATTACHED`同時指定。 適用於 Visual Studio 2005 和更新版本。

## <a name="remarks"></a>備註

用於`Flags`隸屬[PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)結構。

這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求

標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱

- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)