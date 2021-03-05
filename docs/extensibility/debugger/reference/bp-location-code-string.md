---
description: 用來根據使用者可從整合式開發環境輸入的字串來設定程式碼中斷點 (IDE) 。
title: BP_LOCATION_CODE_STRING |Microsoft 檔
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
ms.openlocfilehash: 9508a4a83894757fb47e35d8db7334bfb144ff59
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144373"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
用來根據使用者可從整合式開發環境輸入的字串來設定程式碼中斷點 (IDE) 。

## <a name="syntax"></a>語法

```cpp
typedef struct _BP_LOCATION_CODE_STRING {
    BSTR bstrContext;
    BSTR bstrCodeExpr;
} BP_LOCATION_CODE_STRING;
```

## <a name="members"></a>成員
`bstrContext`\
程式碼內中斷點的內容，通常是在呼叫堆疊上看到的方法或函式名稱。

`bstrCodeExpr`\
使用者輸入以描述程式碼中斷點的字串。

## <a name="remarks"></a>備註
此結構是 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) 結構的成員，做為聯集的一部分。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [Structures and Unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
