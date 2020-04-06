---
title: CONTEXT_INFO_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737599"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
指定要檢索有關記憶體上下文的資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>欄位
`CIF_MODULEURL`\
初始化/使用`bstrModuleUrl`[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構的欄位。

`CIF_FUNCTION`\
初始化/使用`bstrFunction`結構欄位`CONTEXT_INFO`。

`CIF_FUNCTIONOFFSET`\
初始化/使用`posFunctionOffset`結構欄位`CONTEXT_INFO`。

`CIF_ADDRESS`\
初始化/使用`bstrAddress`結構欄位`CONTEXT_INFO`。

`CIF_ADDRESSOFFSET`\
初始化/使用`bstrAddressOffset`結構欄位`CONTEXT_INFO`。

`CIF_ALLFIELDS`\
初始化/使用`CONTEXT_INFO`結構的所有欄位。

## <a name="remarks"></a>備註
這些值將參數傳遞給[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)方法,以指示要初始化[CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)結構的欄位。

這些標誌還用於指示在返回`CONTEXT_INFO`結構時使用結構的欄位並有效。

這些值可以與位或組合。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
