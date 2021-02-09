---
title: DEBUG_REASON |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d2ce7eeb28627f7cb0a1dfbe399bd55f04ff7be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921235"
---
# <a name="debug_reason"></a>DEBUG_REASON
指定啟動處理常式以進行偵錯工具的原因。

## <a name="syntax"></a>Syntax

```cpp
enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
typedef DWORD DEBUG_REASON;
```

```csharp
public enum enum_DEBUG_REASON {
    DEBUG_REASON_ERROR         = 0,
    DEBUG_REASON_USER_LAUNCHED = 1,
    DEBUG_REASON_USER_ATTACHED = 2,
    DEBUG_REASON_AUTO_ATTACHED = 3,
    DEBUG_REASON_CAUSALITY     = 4
};
```

## <a name="fields"></a>欄位
`DEBUG_REASON_ERROR`\
發生非特定的錯誤 (當其他原因都不符合) 時，就會使用此錯誤作為預設條件。

`DEBUG_REASON_USER_LAUNCHED`\
此程式是在使用者的要求上啟動。

`DEBUG_REASON_USER_ATTACHED`\
已由使用者附加已在執行中的進程。

`DEBUG_REASON_AUTO_ATTACHED`\
進程會在啟動時自動附加至。

`DEBUG_REASON_CAUSALITY`\
此程式是因為及時 (JIT) 的調試 *程式* 而啟動。

## <a name="remarks"></a>備註
從 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) 方法傳回。

## <a name="requirements"></a>規格需求
標頭： msdbg。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)
