---
title: PROVIDER_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 67c055c1cf9fffde227d4e52a9764b2559a2342b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864788"
---
# <a name="providerfields"></a>PROVIDER_FIELDS
指定的程式提供者相關聯的屬性。

## <a name="syntax"></a>語法

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="members"></a>成員
 PFIELD_PROGRAM_NODES`ProgramNodes`欄位無效。

 PFIELD_IS_DEBUGGER_PRESENT`fIsDebuggerPresent`欄位無效。

## <a name="remarks"></a>備註
 這些值會傳回在`Fields`隸屬[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構，以表示哪些欄位結構的明確已填入。

 這些值可以合併的位元`OR`。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)