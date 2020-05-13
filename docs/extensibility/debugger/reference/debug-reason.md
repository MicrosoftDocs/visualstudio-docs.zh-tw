---
title: DEBUG_REASON |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59954ea7e89390a5e35dbe0bfb0412da1aabc80f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737429"
---
# <a name="debug_reason"></a>DEBUG_REASON
指定啟動進程以進行調試的原因。

## <a name="syntax"></a>語法

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>欄位
`DEBUG_REASON_ERROR`\
發生非特定錯誤(當其他原因均不合適時,這用作默認條件)。

`DEBUG_REASON_USER_LAUNCHED`\
該過程是應使用者請求啟動的。

`DEBUG_REASON_USER_ATTACHED`\
已運行的進程由使用者附加到。

`DEBUG_REASON_AUTO_ATTACHED`\
該過程在啟動時自動附加到。

`DEBUG_REASON_CAUSALITY`\
此過程是由於即時 (JIT) 除錯事件而啟動*的*。

## <a name="remarks"></a>備註
從[GetDebugAthe 方法](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)返回。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
