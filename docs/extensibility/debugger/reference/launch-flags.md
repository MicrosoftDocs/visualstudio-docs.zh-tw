---
title: LAUNCH_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- LAUNCH_FLAGS
helpviewer_keywords:
- LAUNCH_FLAGS enumeration
ms.assetid: f51aab02-d257-4302-bb79-b7d8ba9ac4e5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f18fb850641391f451f5eedb08b7130566dd4de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714710"
---
# <a name="launch_flags"></a>LAUNCH_FLAGS
指定調試啟動標誌。

## <a name="syntax"></a>語法

```cpp
enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
typedef DWORD LAUNCH_FLAGS;
```

```csharp
public enum enum_LAUNCH_FLAGS {
    LAUNCH_DEBUG      = 0x0000,
    LAUNCH_NODEBUG    = 0x0001,
    LAUNCH_ENABLE_ENC = 0x0002,
    LAUNCH_MERGE_ENV  = 0x0004
};
```

## <a name="fields"></a>欄位
`LAUNCH_DEBUG`\
啟動調試過程。

`LAUNCH_NODEBUG`\
啟動進程而不調試它。

`LAUNCH_ENABLE_ENC`\
棄用,請勿使用。

`LAUNCH_MERGE_ENV`\
啟動進程並將環境與啟動主機合併。

## <a name="remarks"></a>備註
這些值作為參數傳遞給[Launch 暫停](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法。

這些旗標可以稍微`OR`結合 。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
