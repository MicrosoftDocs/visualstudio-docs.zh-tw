---
title: 在啟動後傳送啟動事件 |Microsoft Docs
description: 瞭解在偵錯工具附加至程式之後，debug engine 傳送至 debug 會話的一系列啟動事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e5263c696f9f76c71463538d56414702e616a670
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960841"
---
# <a name="send-startup-events-after-a-launch"></a>在啟動後傳送啟動事件
一旦將 debug engine (DE) 附加至程式之後，它就會將一連串的啟動事件傳送回 debug 會話。

 傳送回 debug 會話的啟動事件包括：

- 引擎建立事件。

- 程式建立事件。

- 執行緒建立和模組載入事件。

- 載入完成事件，會在程式碼載入並準備好執行時，但在執行任何程式碼之前傳送。

  > [!NOTE]
  > 當此事件繼續時，會初始化全域變數，並執行啟動常式。

- 可能有其他執行緒建立和模組載入事件。

- 進入點事件，表示程式已到達其主要進入點，例如 **main** 或 `WinMain` 。 如果取消附加至已在執行中的程式，通常不會傳送此事件。

  先以程式設計的方式，先將會話 debug manager (SDM 傳送) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 介面（代表引擎建立事件），後面接著 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)（代表程式建立事件）。

  這些事件通常會接著一或多個 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 執行緒建立事件和 [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) 模組載入事件。

  當程式碼已載入且準備好要執行，但在執行任何程式碼之前，會先將 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 載入完成事件傳送給 SDM。 最後，如果程式尚未執行，則會傳送 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 進入點事件，以通知程式已到達其主要進入點，並已準備好進行偵測。

## <a name="see-also"></a>另請參閱
- [執行的控制](../../extensibility/debugger/control-of-execution.md)
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
