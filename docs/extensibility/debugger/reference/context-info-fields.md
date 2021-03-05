---
description: 指定要對記憶體內容取得哪些資訊。
title: CONTEXT_INFO_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 401195d5b03f87ba1ea5c66811570a720e53bdae
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170766"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
指定要對記憶體內容取得哪些資訊。

## <a name="syntax"></a>Syntax

```cpp
enum enum_CONTEXT_INFO_FIELDS {
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
初始化/使用 `bstrModuleUrl` [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 結構的欄位。

`CIF_FUNCTION`\
初始化/使用 `bstrFunction` 結構的欄位 `CONTEXT_INFO` 。

`CIF_FUNCTIONOFFSET`\
初始化/使用 `posFunctionOffset` 結構的欄位 `CONTEXT_INFO` 。

`CIF_ADDRESS`\
初始化/使用 `bstrAddress` 結構的欄位 `CONTEXT_INFO` 。

`CIF_ADDRESSOFFSET`\
初始化/使用 `bstrAddressOffset` 結構的欄位 `CONTEXT_INFO` 。

`CIF_ALLFIELDS`\
初始化/使用結構的所有欄位 `CONTEXT_INFO` 。

## <a name="remarks"></a>備註
這些值會以參數傳遞給 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 方法，以指出要初始化 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 結構的哪些欄位。

這些旗標也可用來指出 `CONTEXT_INFO` 當傳回結構時，所使用的結構欄位和有效的欄位。

這些值可能會與位 OR 合併。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
