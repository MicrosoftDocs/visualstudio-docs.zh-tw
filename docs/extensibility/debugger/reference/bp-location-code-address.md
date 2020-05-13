---
title: BP_LOCATION_CODE_ADDRESS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_ADDRESS
helpviewer_keywords:
- BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: c215630e522adabdbd285e00d4bcd87cae22a931
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738034"
---
# <a name="bp_location_code_address"></a>BP_LOCATION_CODE_ADDRESS
描述代碼中地址的斷點位置。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_CODE_ADDRESS {
    BSTR bstrContext;
    BSTR bstrModuleUrl;
    BSTR bstrFunction;
    BSTR bstrAddress;
} BP_LOCATION_CODE_ADDRESS;
```

## <a name="members"></a>成員
`bstrContext`\
斷點的上下文,通常是在調用堆疊上看到的方法或函數名稱。

`bstrModuleUrl`\
包含斷點的模組的 URL。

`bstrFunction`\
包含斷點的函數的名稱。

`bstrAddress`\
斷點的位址,由表達式賦值器解析,以將其綁定到[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。

## <a name="remarks"></a>備註
此結構是作為聯合的一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
