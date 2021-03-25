---
description: 用來描述模組。
title: MODULE_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b78e0ec9f720307a60485283b98939dee954ff29
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079783"
---
# <a name="module_flags"></a>MODULE_FLAGS
用來描述模組。

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>欄位
 `MODULE_FLAG_NONE`\
 未指定模組。

 `MODULE_FLAG_SYSTEM`\
 指定系統模組。

 `MODULE_FLAG_SYMBOLS`\
 指定符號模組。

 `MODULE_FLAG_64BIT`\
 指定64位模組。

 `MODULE_FLAG_OPTIMIZED`\
 指定模組已經過優化。 此狀態會反映在 [ **模組** ] 視窗中。

 `MODULE_FLAG_UNOPTIMIZED`\
 指定尚未優化的模組。 此狀態會反映在 [ **模組** ] 視窗中。 這是預設狀態。

## <a name="remarks"></a>備註
 用於 `m_dwModuleFlags` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 結構的成員。

 這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
