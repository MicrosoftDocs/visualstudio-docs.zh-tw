---
title: BP_FLAGS90 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738054"
---
# <a name="bp_flags90"></a>BP_FLAGS90
列舉選擇性旗標的有效值。 當您設定中斷點時，可以使用選擇性旗標來指定其他資訊。 此列舉會擴充 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 列舉。

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
指定無中斷點旗標。

`BP90_FLAG_MAP_DOCPOSITION`\
指定 debug engine (DE) 應該使用檔位置來對應中斷點。 這僅適用于以腳本導向的原始程式檔中設定的中斷點，例如 Active Server Pages (ASP) 。

`BP90_FLAG_DONT_STOP`\
指定應該由 debug 引擎處理中斷點，但 debug engine 最後不應該停止，也就是說，不應傳送 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) 事件物件。 此旗標設計主要用於追蹤點。

`BP90_FLAG_TRACEPOINT_CONTINUE`\
由原生偵錯工具引擎用來判斷是否應該清除逐步執行狀態。 它不同于 BP90_FLAG_DONT_STOP，因為如果追蹤點執行宏，則不會設定 BP90_FLAG_DONT_STOP。

## <a name="requirements"></a>需求
標頭： Msdbg90。h

命名空間： VisualStudio

元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [列舉](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
