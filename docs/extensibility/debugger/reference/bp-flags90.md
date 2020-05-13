---
title: BP_FLAGS90 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5628af4a6e5c4deae3de02340e882bd2605e22d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738054"
---
# <a name="bp_flags90"></a>BP_FLAGS90
枚舉可選標誌的有效值。 設置斷點時,可選標誌可用於指定其他資訊。 此枚舉擴展了[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)枚舉。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE               = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION    = 0x0001,
    BP90_FLAG_DONT_STOP          = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
typedef DWORD BP_FLAGS90;
```

```csharp
public enum enum_BP_FLAGS90
{
    // VS 8.0 values
    BP90_FLAG_NONE                = 0x0000,
    BP90_FLAG_MAP_DOCPOSITION     = 0x0001,
    BP90_FLAG_DONT_STOP           = 0x0002,

    // Values added in VS 9.0
    BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,
};
```

## <a name="fields"></a>欄位
`BP90_FLAG_NONE`\
指定無斷點標誌。

`BP90_FLAG_MAP_DOCPOSITION`\
指定除錯引擎 (DE) 應使用文件位置映射斷點。 這僅適用於在面向腳稿的源檔中設置的斷點,如活動伺服器頁 (ASP)。

`BP90_FLAG_DONT_STOP`\
指定斷點應由調試引擎處理,但調試引擎最終不應停止;也就是說,不應發送[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)事件物件。 此標誌設計主要用於跟蹤點。

`BP90_FLAG_TRACEPOINT_CONTINUE`\
本機調試引擎用於確定是否應清除步進狀態。 它與BP90_FLAG_DONT_STOP不同,因為如果跟蹤點執行宏,則不設置BP90_FLAG_DONT_STOP。

## <a name="requirements"></a>需求
標題: Msdbg90.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
