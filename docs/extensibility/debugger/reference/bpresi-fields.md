---
title: BPRESI_FIELDS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d82650fabf467d44b1bd5eba01599c5cb5e40bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938259"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
指定要抓取的資訊，以取得中斷點的成功解析。

## <a name="syntax"></a>Syntax

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
初始化/使用 `bpResLocation` [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 結構的 (中斷點解析位置) 欄位。

`BPRESI_PROGRAM`\
初始化/使用 `pProgram` 結構的欄位 `BP_RESOLUTION_INFO` 。

`BPRESI_THREAD`\
初始化/使用 `pThread` 結構的欄位 `BP_RESOLUTION_INFO` 。

`BPRESI_ALLFIELDS`\
指定所有欄位。

## <a name="remarks"></a>備註
傳遞至 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) 方法，以指出要初始化 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) 結構的哪些欄位。

這些旗標也可用來指出 `BP_RESOLUTION_INFO` 當傳回該結構時，要使用和有效的結構欄位。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
