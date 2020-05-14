---
title: CANSTOP_REASON |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d7be361d4468584c109db52f487b3de3c1fdff0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737690"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
用於確定程式在到達執行中的特定點后是否可以停止執行。

## <a name="syntax"></a>語法

```cpp
enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
typedef DWORD CANSTOP_REASON;
```

```csharp
public enum enum_CANSTOP_REASON {
    CANSTOP_ENTRYPOINT = 0x0000,
    CANSTOP_STEPIN     = 0x0001
};
```

## <a name="fields"></a>欄位
`CANSTOP_ENTRYPOINT`\
指定給定程式的入口點。

`CANSTOP_STEPIN`\
指定單步執行到函數。

## <a name="remarks"></a>備註
作為參數傳遞給[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)方法,以與會話調試管理器 (SDM) 確認是否可以在到達程式的入口點後或踏入函數或方法后停止。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
