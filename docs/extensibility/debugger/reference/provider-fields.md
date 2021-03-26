---
description: 指定與程式提供者相關聯的屬性。
title: PROVIDER_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_FIELDS
helpviewer_keywords:
- PROVIDER_FIELDS enumeration
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a1ab410d9780078cd786b75f14d0321498eca8fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079536"
---
# <a name="provider_fields"></a>PROVIDER_FIELDS
指定與程式提供者相關聯的屬性。

## <a name="syntax"></a>Syntax

```cpp
enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
typedef DWORD PROVIDER_FIELDS;
```

```csharp
public enum enum_PROVIDER_FIELDS {
   PFIELD_PROGRAM_NODES       = 0x01,
   PFIELD_IS_DEBUGGER_PRESENT = 0x02
};
```

## <a name="fields"></a>欄位
 `PFIELD_PROGRAM_NODES`\
 `ProgramNodes`欄位有效。

 `PFIELD_IS_DEBUGGER_PRESENT`\
 `fIsDebuggerPresent`欄位有效。

## <a name="remarks"></a>備註
 這些值會在 `Fields` [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 結構的成員中傳回，以指出已明確填入結構的欄位。

 這些值可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
