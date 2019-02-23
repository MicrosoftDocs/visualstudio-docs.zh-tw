---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 488c2b1a96d01e0e7dfa9868d2f7e5111adc4e2d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699427"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
指定要擷取失敗的解決方式的中斷點相關的資訊。

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

## <a name="members"></a>成員
初始化/使用 PERESI_BPRESLOCATION `bpResLocation` （中斷點解析位置） 欄位[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構。

初始化/使用 BPERESI_PROGRAM`pProgram`欄位`BP_ERROR_RESOLUTION_INFO`結構。

初始化/使用 BPERESI_THREAD`pThread`欄位`BP_ERROR_RESOLUTION_INFO`結構。

初始化/使用 BPERESI_MESSAGE`bstrMessage`欄位`BP_ERROR_RESOLUTION_INFO`結構。

初始化/使用 BPERESI_TYPE `dwType` （中斷點型別） 欄位`BP_ERROR_RESOLUTION_INFO`結構。

BPERESI_ALLFIELDS 初始化/使用的所有欄位`BP_ERROR_RESOLUTION_INFO`結構。

## <a name="remarks"></a>備註
做為參數傳遞[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)方法，以表示哪些欄位[BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)結構會進行初始化。

這些值也可用來指示中的哪些欄位`BP_ERROR_RESOLUTION_INFO`結構會使用和有效時傳回該結構。

這些值可能會合併的位元`OR`。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
