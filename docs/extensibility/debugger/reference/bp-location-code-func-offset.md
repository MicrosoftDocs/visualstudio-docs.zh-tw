---
title: BP_LOCATION_CODE_FUNC_OFFSET |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET
helpviewer_keywords:
- BP_LOCATION_CODE_FUNC_OFFSET structure
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 32331a5b628c27dc79d6a2e5919c8d268c96a3aa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738003"
---
# <a name="bp_location_code_func_offset"></a>BP_LOCATION_CODE_FUNC_OFFSET
描述代碼中函數中斷點的偏移位置。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {
    BSTR                     bstrContext;
    IDebugFunctionPosition2* pFuncPos;
} BP_LOCATION_CODE_FUNC_OFFSET;
```

## <a name="members"></a>成員
`bstrContext`\
斷點的上下文,通常是在調用堆疊上看到的方法或函數名稱。

`pFuncPos`\
[IDebug函數位置2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)物件,它描述函數的名稱和從函數開頭的相對位置。

## <a name="remarks"></a>備註
此結構是作為聯合的一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的成員。

該`pFuncPos`成員指示在何處設置函數斷點。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)
