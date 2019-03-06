---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3ec96c5ba806e6eff735edc8093868b19ebaf5b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681396"
---
# <a name="moduleflags"></a>MODULE_FLAGS
用來描述模組。

## <a name="syntax"></a>語法

```cpp
enum enum_MODULE_FLAGS { 
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
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="members"></a>成員
 MODULE_FLAG_NONE 指定沒有模組。

 MODULE_FLAG_SYSTEM 指定系統模組。

 MODULE_FLAG_SYMBOLS 指定符號的模組。

 MODULE_FLAG_64BIT 指定 64 位元模組。

 MODULE_FLAG_OPTIMIZED 指定了模組已經過最佳化。 此狀態會反映在**模組**視窗。

 MODULE_FLAG_UNOPTIMIZED 指定了模組尚未經過最佳化。 此狀態會反映在**模組**視窗。 這是預設狀態。

## <a name="remarks"></a>備註
 用於`m_dwModuleFlags`隸屬[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構。

 這些旗標可能會結合的位元`OR`。

## <a name="requirements"></a>需求
 標頭： msdbg.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)