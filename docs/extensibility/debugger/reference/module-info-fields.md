---
title: MODULE_INFO_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714321"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
指定除錯模組資訊的標誌。

## <a name="syntax"></a>語法

```cpp
enum enum_MODULE_INFO_FIELDS { 
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
public enum enum_MODULE_INFO_FIELDS { 
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
 初始化/使用結構中沒有任何欄位。

 `MIF_NAME`\
 初始化/使用`m_bstrName`[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構中的欄位。

 `MIF_URL`\
 初始化/使用結構`m_bstrUrl``MODULE_INFO`中的 欄位。

 `MIF_VERSION`\
 初始化/使用結構`m_bstrVersion``MODULE_INFO`中的 欄位。

 `MIF_DEBUGMESSAGE`\
 初始化/使用結構`m_bstrDebugMessage``MODULE_INFO`中的 欄位。

 `MIF_LOADADDRESS`\
 初始化/使用結構`m_addrLoadAddress``MODULE_INFO`中的 欄位。

 `MIF_PREFFEREDADDRESS`\
 初始化/使用結構`m_addrPreferredLoadAddress``MODULE_INFO`中的 欄位。

 `MIF_SIZE`\
 初始化/使用結構`m_dwSize``MODULE_INFO`中的 欄位。

 `MIF_LOADORDER`\
 初始化/使用結構`m_dwLoadOrder``MODULE_INFO`中的 欄位。

 `MIF_TIMESTAMP`\
 初始化/使用結構`m_TimeStamp``MODULE_INFO`中的 欄位。

 `MIF_URLSYMBOLLOCATION`\
 初始化/使用結構`m_bstrUrlSymbolLocation``MODULE_INFO`中的 欄位。

 `MIF_FLAGS`\
 初始化/使用結構`m_dwModuleFlags``MODULE_INFO`中的 欄位。

 `MIF_ALLFIELDS`\
 初始化/使用`MODULE_INFO`結構中的所有欄位。

## <a name="remarks"></a>備註
 這些值作為參數傳遞給[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)方法,以指示要初始化[MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)結構的欄位。

 這些值還用於結構中`MODULE_INFO`,以指示使用哪些欄位有效。

 這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
 標題: msdbg.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
