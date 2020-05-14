---
title: PROVIDER_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37f64b455ab0331f9b8f08da1f29a3e2c1b82fdf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713793"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
指定與程式提供程式關聯的屬性。

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

## <a name="fields"></a>欄位
 `PFIELD_PROGRAM_NODES`\
 該`ProgramNodes`欄位有效。

 `PFIELD_IS_DEBUGGER_PRESENT`\
 該`fIsDebuggerPresent`欄位有效。

## <a name="remarks"></a>備註
 這些值在`Fields`[PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)結構的成員中返回,以指示已顯式填充結構的欄位。

 這些值可以與一點一點地`OR`結合。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
