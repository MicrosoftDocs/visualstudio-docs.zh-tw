---
description: 指定要取出哪些有關 debug 屬性物件的資訊。
title: DEBUGPROP_INFO_FLAGS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 63467e93b80648e6a00728dc66971b7c9b3c9b24
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170519"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
指定要取出哪些有關 debug 屬性物件的資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>欄位
`DEBUGPROP_INFO_FULLNAME`\
初始化/使用 `bstrFullName` 欄位。

`DEBUGPROP_INFO_NAME`\
初始化/使用 `bstrName` 欄位。

`DEBUGPROP_INFO_TYPE`\
初始化/使用 `bstrType` 欄位。

`DEBUGPROP_INFO_VALUE`\
初始化/使用 `bstrValue` 欄位。

`DEBUGPROP_INFO_ATTRIB`\
初始化/使用 `dwAttrib` 欄位。

`DEBUGPROP_INFO_PROP`\
初始化/使用 `pProperty` 包含 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 介面的欄位。

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
指定值欄位應該包含此類型之物件的自動展開值（如果有的話）。

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
已取代。

`DEBUGPROP_INFO_VALUE_RAW`\
請勿傳回任何 beautified 值或成員 (也就是不要將值格式化) 。

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
請勿傳回任何特殊的合成值 (例如，請勿呼叫 `ToString()` 物件來產生) 的值。

`DEBUGPROP_INFO_NONE`\
指定不設定任何旗標。

`DEBUGPROP_INFO_STANDARD`\
初始化/使用 `dwAttrib` 、、 `bstrName` `bstrType` 和 `bstrValue` 欄位。

`DEBUGPROP_INFO_All`\
表示所有旗標的遮罩。

## <a name="remarks"></a>備註
這些值會傳遞至 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)和 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) 方法，以指出哪些欄位要初始化 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 結構。

這些值也會用於結構的 `dwFields` 成員 `DEBUG_PROPERTY_INFO` ，以指出在傳回結構時使用結構的欄位和有效的欄位。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
