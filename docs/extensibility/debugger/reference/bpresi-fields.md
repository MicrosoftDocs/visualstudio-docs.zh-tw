---
title: BPRESI_FIELDS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737729"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
指定要檢索的資訊,說明斷點的成功解析。

## <a name="syntax"></a>語法

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>欄位
`BPRESI_BPRESLOCATION`\
初始化/使用`bpResLocation`[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構的(斷點解析度位置)欄位。

`BPRESI_PROGRAM`\
初始化/使用`pProgram`結構欄位`BP_RESOLUTION_INFO`。

`BPRESI_THREAD`\
初始化/使用`pThread`結構欄位`BP_RESOLUTION_INFO`。

`BPRESI_ALLFIELDS`\
指定所有欄位。

## <a name="remarks"></a>備註
傳遞給[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)方法,指示要初始化[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)結構的欄位。

這些標誌還用於指示在返回該結構時使用`BP_RESOLUTION_INFO`結構的欄位並有效。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
