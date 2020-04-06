---
title: BP_LOCATION_DATA_STRING |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 75f881feaaa2068abd98d771a63024f20435d98f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737977"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
用於設置基於使用者可以從整合式開發環境 (IDE) 輸入的字串的數據斷點。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_DATA_STRING {
    IDebugThread2* pThread;
    BSTR           bstrContext;
    BSTR           bstrDataExpr;
    DWORD          dwNumElements;
} BP_LOCATION_DATA_STRING;
```

## <a name="members"></a>成員
`pThread`\
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件,表示發生斷點的線程。

`bstrContext`\
代碼中的斷點的上下文,通常是調用堆疊上看到的方法或函數名稱。

`bstrDataExpr`\
使用者輸入的數據字串來設置斷點。

`dwNumElements`\
發生斷點的資料字串中的元素數。

## <a name="remarks"></a>備註
此結構是作為聯合的一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
