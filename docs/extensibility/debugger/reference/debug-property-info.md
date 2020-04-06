---
title: DEBUG_PROPERTY_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34fc1b5103949a767a3ee448618cbb708ea6a48b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737457"
---
# <a name="debug_property_info"></a>DEBUG_PROPERTY_INFO
包含有關調試屬性的資訊。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDEBUG_PROPERTY_INFO {
    DEBUGPROP_INFO_FLAGS dwValidFields;
    BSTR                 bstrFullName;
    BSTR                 bstrName;
    BSTR                 bstrType;
    BSTR                 bstrValue;
    IDebugProperty2*     pProperty;
    DBG_ATTRIB_FLAGS     dwAttrib;
} DEBUG_PROPERTY_INFO;
```

```csharp
public struct DEBUG_PROPERTY_INFO {
    public uint            dwValidFields;
    public string          bstrFullName;
    public string          bstrName;
    public string          bstrType;
    public string          bstrValue;
    public IDebugProperty2 pProperty;
    public ulong           dwAttrib;
};
```

## <a name="members"></a>成員
`dwValidFields`\
[DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)枚舉中的標誌的組合,用於指定填充哪些欄位。

`bstrFullName`\
屬性的全名。

`bstrName`\
上下文中的屬性名稱。

`bstrType`\
屬性類型作為格式化字串。

`bstrValue`\
屬性值作為格式化字串。

`pProperty`\
此結構描述的[IDebug Property2](../../../extensibility/debugger/reference/idebugproperty2.md)物件。

`dwAttrib`\
描述此屬性屬性[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)枚舉的標誌的組合。

## <a name="remarks"></a>備註
屬性是具有名稱、類型和值的分層性質的物件。 例如,屬性可以描述局部變數、參數、監視變數和運算式以及寄存器。

此結構傳遞給填寫該結構的[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)方法。 此結構還作為此結構清單的一部分從[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)介面返回,該介面又從調用[Enum 子項](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)和[枚舉屬性](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)方法返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [取得財產資訊](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
