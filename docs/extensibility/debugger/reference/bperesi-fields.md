---
title: BPERESI_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737761"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
指定要檢索有關斷點解析失敗的資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>欄位
`PERESI_BPRESLOCATION`\
初始化/使用`bpResLocation`[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構的(斷點解析度位置)欄位。

`BPERESI_PROGRAM`\
初始化/使用`pProgram`結構欄位`BP_ERROR_RESOLUTION_INFO`。

`BPERESI_THREAD`\
初始化/使用`pThread`結構欄位`BP_ERROR_RESOLUTION_INFO`。

`BPERESI_MESSAGE`\
初始化/使用`bstrMessage`結構欄位`BP_ERROR_RESOLUTION_INFO`。

`BPERESI_TYPE`\
初始化/使用`dwType``BP_ERROR_RESOLUTION_INFO`結構的(斷點類型)欄位。

`BPERESI_ALLFIELDS`\
初始化/使用`BP_ERROR_RESOLUTION_INFO`結構的所有欄位。

## <a name="remarks"></a>備註
作為參數傳遞給[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法,以指示要初始化[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構的欄位。

這些值還用於指示在返回結構時使用結構`BP_ERROR_RESOLUTION_INFO`中的哪些欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
