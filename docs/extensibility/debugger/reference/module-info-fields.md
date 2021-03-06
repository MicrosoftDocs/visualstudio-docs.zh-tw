---
description: 指定 debug 模組資訊的旗標。
title: MODULE_INFO_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc27420fc598d174b8e71c5ed3edd879a4a30d9d
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222363"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
指定 debug 模組資訊的旗標。

## <a name="syntax"></a>Syntax

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>欄位
 `MIF_NONE`\
 初始化/使用結構中的任何欄位。

 `MIF_NAME`\
 初始化/使用 `m_bstrName` [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 結構中的欄位。

 `MIF_URL`\
 初始化/使用 `m_bstrUrl` 結構中的欄位 `MODULE_INFO` 。

 `MIF_VERSION`\
 初始化/使用 `m_bstrVersion` 結構中的欄位 `MODULE_INFO` 。

 `MIF_DEBUGMESSAGE`\
 初始化/使用 `m_bstrDebugMessage` 結構中的欄位 `MODULE_INFO` 。

 `MIF_LOADADDRESS`\
 初始化/使用 `m_addrLoadAddress` 結構中的欄位 `MODULE_INFO` 。

 `MIF_PREFFEREDADDRESS`\
 初始化/使用 `m_addrPreferredLoadAddress` 結構中的欄位 `MODULE_INFO` 。

 `MIF_SIZE`\
 初始化/使用 `m_dwSize` 結構中的欄位 `MODULE_INFO` 。

 `MIF_LOADORDER`\
 初始化/使用 `m_dwLoadOrder` 結構中的欄位 `MODULE_INFO` 。

 `MIF_TIMESTAMP`\
 初始化/使用 `m_TimeStamp` 結構中的欄位 `MODULE_INFO` 。

 `MIF_URLSYMBOLLOCATION`\
 初始化/使用 `m_bstrUrlSymbolLocation` 結構中的欄位 `MODULE_INFO` 。

 `MIF_FLAGS`\
 初始化/使用 `m_dwModuleFlags` 結構中的欄位 `MODULE_INFO` 。

 `MIF_ALLFIELDS`\
 初始化/使用結構中的所有欄位 `MODULE_INFO` 。

## <a name="remarks"></a>備註
 這些值會以引數的形式傳遞至 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) 方法，以指出要初始化 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 結構的哪些欄位。

 結構中也會使用這些值 `MODULE_INFO` 來指出哪些欄位已使用且有效。

 這些旗標可以與位結合 `OR` 。

## <a name="requirements"></a>規格需求
 標頭： msdbg。h

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
