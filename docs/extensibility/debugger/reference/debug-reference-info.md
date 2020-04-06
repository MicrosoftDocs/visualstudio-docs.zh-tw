---
title: DEBUG_REFERENCE_INFO |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REFERENCE_INFO
helpviewer_keywords:
- DEBUG_REFERENCE_INFO structure
ms.assetid: 24b83d00-d756-42a1-8083-730f998761dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6e31205f52151679f932877c9c4fdc56907ea59e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737410"
---
# <a name="debug_reference_info"></a>DEBUG_REFERENCE_INFO
描述引用。

## <a name="syntax"></a>語法

```cpp
typedef struct tagDEBUG_REFERENCE_INFO {
    DEBUGREF_INFO_FLAGS dwFields;
    BSTR                bstrName;
    BSTR                bstrType;
    BSTR                bstrValue;
    DBG_ATTRIB_FLAGS    dwAttrib;
    REFERENCE_TYPE.     dwRefType;
    IDebugReference2*   m_pReference;
} DEBUG_REFERENCE_INFO;
```

```csharp
public struct DEBUG_REFERENCE_INFO {
    public uint             dwFields;
    public string           bstrName;
    public string           bstrType;
    public string           bstrValue;
    public ulong            dwAttrib;
    public uint.            dwRefType;
    public IDebugReference2 m_pReference;
};
```

## <a name="members"></a>成員
`dwFields`\
[DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)枚舉中的標誌的組合,用於指定填寫哪些欄位。

`bstrName`\
[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件的使用者指定名稱。

`bstrType`\
作為格式化字串的引用類型。

`bstrValue`\
為格式化字串的引言值

`dwAttrib`\
[DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)枚舉中標記的組合,用於指定調試屬性屬性的標誌。

`dwRefType`\
REFERENCE_TYPE[枚舉中](../../../extensibility/debugger/reference/reference-type.md)的值,用於指定引用類型是強還是弱。

`m_pReference`\
指定引用資訊的[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)物件。

## <a name="remarks"></a>備註
此結構傳遞給要填充的[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)方法的調用。 此結構也作為[IEnumDebugReference Info2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)介面清單的一部分返回,該介面又從對[Enum 兒童](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)方法的調用返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
