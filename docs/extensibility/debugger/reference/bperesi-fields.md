---
description: 指定要抓取的資訊，以找出中斷點的解析失敗。
title: BPERESI_FIELDS |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e26b5a7285c2e5c9135429777b4b58f35252e550
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162520"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
指定要抓取的資訊，以找出中斷點的解析失敗。

## <a name="syntax"></a>Syntax

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
初始化/使用 `bpResLocation` [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 結構的 (中斷點解析位置) 欄位。

`BPERESI_PROGRAM`\
初始化/使用 `pProgram` 結構的欄位 `BP_ERROR_RESOLUTION_INFO` 。

`BPERESI_THREAD`\
初始化/使用 `pThread` 結構的欄位 `BP_ERROR_RESOLUTION_INFO` 。

`BPERESI_MESSAGE`\
初始化/使用 `bstrMessage` 結構的欄位 `BP_ERROR_RESOLUTION_INFO` 。

`BPERESI_TYPE`\
初始化/使用 `dwType` 結構的 (中斷點類型) 欄位 `BP_ERROR_RESOLUTION_INFO` 。

`BPERESI_ALLFIELDS`\
初始化/使用結構的所有欄位 `BP_ERROR_RESOLUTION_INFO` 。

## <a name="remarks"></a>備註
以參數形式傳遞至 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) 方法，以指出要初始化 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) 結構的哪些欄位。

這些值也可用來指出 `BP_ERROR_RESOLUTION_INFO` 當傳回該結構時，會使用結構中的哪些欄位以及有效的欄位。

這些值可能會與位結合 `OR` 。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
