---
title: BP_FLAGS |微軟文件
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62626ff75a4545d89835d3136649191004291f8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738056"
---
# <a name="bp_flags"></a>BP_FLAGS
提供可選標誌,用於在設置斷點時指定其他資訊。

## <a name="syntax"></a>語法

```cpp
enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
typedef DWORD BP_FLAGS;
```

```csharp
public enum enum_BP_FLAGS {
    BP_FLAG_NONE            = 0x0000,
    BP_FLAG_MAP_DOCPOSITION = 0x0001,
    BP_FLAG_DONT_STOP       = 0x0002
};
```

## <a name="fields"></a>欄位
`BP_FLAG_NONE`\
指定無斷點標誌。

`BP_FLAG_MAP_DOCPOSITION`\
指定除錯引擎 (DE) 應使用文件位置映射斷點。 這僅適用於在面向腳稿的源檔中設置的斷點,如活動伺服器頁 (ASP)。

`BP_FLAG_DONT_STOP`\
指定斷點應由調試引擎處理,但調試引擎最終不應停止於此(即,不應發送[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)事件物件)。 此標誌設計主要用於跟蹤點。

## <a name="remarks"></a>備註
用於`dwFlags`[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)和[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)結構的成員。

這些值可以稍微結合`OR`。

## <a name="requirements"></a>需求
標題: msdbg.h

命名空間:微軟.VisualStudio.調試器.互通

程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
