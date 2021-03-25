---
description: 指定要針對特定電腦取出的資訊類型。
title: MACHINE_INFO_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3361ed090dc724f948d98aa0037949e0c573d56d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057932"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
指定要針對特定電腦取出的資訊類型。

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>欄位
 `MCIF_NAME`\
 初始化/使用 `bstrName` 結構中的欄位。

 `MCIF_FLAGS`\
 初始化/使用 `Flags` 結構中的欄位。

 `MIF_ALL`\
 初始化/使用結構中的所有欄位。

## <a name="remarks"></a>備註
 這些值會傳遞至 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 方法，以指出要初始化 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 結構的哪些成員。

 也可用於結構的成員中， `Fields` `MACHINE_INFO` 以指出哪些欄位已使用且有效。

 這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
