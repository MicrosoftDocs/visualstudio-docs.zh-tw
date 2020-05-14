---
title: BP_LOCATION_CODE_STRING |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 0fc0d9a053faf69fde500333ab0faafa0e8d3448
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737978"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
用於根據使用者可以從整合式開發環境 (IDE) 輸入的字串設定代碼斷點。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>成員
`bstrContext`\
代碼中的斷點的上下文,通常是調用堆疊上看到的方法或函數名稱。

`bstrCodeExpr`\
使用者鍵入以描述代碼斷點的字串。

## <a name="remarks"></a>備註
此結構是作為聯合的一部分[BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)結構的成員。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
