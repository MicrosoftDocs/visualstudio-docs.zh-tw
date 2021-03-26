---
description: 用來設定資料中斷點，這些中斷點是以使用者可從整合式開發環境輸入的字串為基礎 (IDE) 。
title: BP_LOCATION_DATA_STRING |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 98cfb12649fe85ce9e5f6b6a51a8c61243b5e9da
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096755"
---
# <a name="bp_location_data_string"></a>BP_LOCATION_DATA_STRING
用來設定資料中斷點，這些中斷點是以使用者可從整合式開發環境輸入的字串為基礎 (IDE) 。

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
代表中斷點發生所在之執行緒的 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) 物件。

`bstrContext`\
程式碼內中斷點的內容，通常是在呼叫堆疊上看到的方法或函式名稱。

`bstrDataExpr`\
使用者輸入以設定中斷點的資料字串。

`dwNumElements`\
發生中斷點的資料字串中的元素數目。

## <a name="remarks"></a>備註
此結構是 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 結構的成員，做為聯集的一部分。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
