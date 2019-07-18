---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: cf8e2958f55ca13ab050302a24ad9e5ae185d81a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353099"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
用於設定資料中斷點的使用者可以輸入從整合式的開發環境 (IDE) 的字串為基礎。

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
[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)物件，表示中斷點發生的執行緒。

`bstrContext`\
程式碼內的中斷點，通常是方法或函式的名稱為 呼叫堆疊上看到的內容。

`bstrDataExpr`\
資料字串，使用者會進入設定中斷點。

`dwNumElements`\
中斷點會發生的資料字串中的項目數目。

## <a name="remarks"></a>備註
此結構是隸屬[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的聯集的一部分。

## <a name="requirements"></a>需求
標頭： msdbg.h

命名空間：Microsoft.VisualStudio.Debugger.Interop

組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [結構和等位](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
