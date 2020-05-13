---
title: DEBUGPROP_INFO_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737401"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
指定要檢索的有關調試屬性物件的哪些資訊。

## <a name="syntax"></a>語法

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
初始化/使用`bstrFullName`欄位。

`DEBUGPROP_INFO_NAME`\
初始化/使用`bstrName`欄位。

`DEBUGPROP_INFO_TYPE`\
初始化/使用`bstrType`欄位。

`DEBUGPROP_INFO_VALUE`\
初始化/使用`bstrValue`欄位。

`DEBUGPROP_INFO_ATTRIB`\
初始化/使用`dwAttrib`欄位。

`DEBUGPROP_INFO_PROP`\
初始化/使用包含`pProperty` [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面的欄位。

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
指定值欄位應包含此類型物件的自動展開值(如果可用)。

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
已被取代。

`DEBUGPROP_INFO_VALUE_RAW`\
不要返回任何美化值或成員(即,不要格式化值)。

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
不要返回任何特殊的合成值(例如,不要調用`ToString()`對象來生成值)。

`DEBUGPROP_INFO_NONE`\
指定不設置任何標誌。

`DEBUGPROP_INFO_STANDARD`\
初始化/使用`dwAttrib``bstrName``bstrType`、`bstrValue`和 欄位。

`DEBUGPROP_INFO_All`\
指示所有標誌的掩碼。

## <a name="remarks"></a>備註
這些值將傳遞給[GetPropertyInfo、Enum](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)[子項](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)和[枚舉屬性](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)方法,以指示要初始化[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構的欄位。

這些值還用於`dwFields``DEBUG_PROPERTY_INFO`結構的成員,以指示在返回結構時使用結構的欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [取得財產資訊](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
