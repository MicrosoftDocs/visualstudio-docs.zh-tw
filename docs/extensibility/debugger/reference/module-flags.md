---
title: MODULE_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714260"
---
# <a name="module_flags"></a>MODULE_FLAGS
用於描述模組。

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

## <a name="fields"></a>欄位
 `MODULE_FLAG_NONE`\
 未指定任何模組。

 `MODULE_FLAG_SYSTEM`\
 指定系統模組。

 `MODULE_FLAG_SYMBOLS`\
 指定符號模組。

 `MODULE_FLAG_64BIT`\
 指定 64 位元模組。

 `MODULE_FLAG_OPTIMIZED`\
 指定模組已優化。 此狀態反映在 **「模組」** 視窗中。

 `MODULE_FLAG_UNOPTIMIZED`\
 指定模組尚未優化。 此狀態反映在 **「模組」** 視窗中。 這是預設狀態。

## <a name="remarks"></a>備註
 用於[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構`m_dwModuleFlags`的成員。

 這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
