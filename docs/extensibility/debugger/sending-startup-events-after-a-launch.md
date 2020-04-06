---
title: 啟動後傳送啟動事件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713005"
---
# <a name="send-startup-events-after-a-launch"></a>啟動後傳送啟動事件
一旦調試引擎 (DE) 連接到程式,它將一系列啟動事件發送回調試會話。

 發回調試工作階段的啟動事件包括:

- 引擎建立事件。

- 程式建立事件。

- 線程創建和模組載入事件。

- 載入完成事件,在載入代碼並準備運行時發送,但在執行任何代碼之前。

  > [!NOTE]
  > 繼續此事件時,將初始化全域變數並運行啟動例程。

- 可能的其他線程創建和模組載入事件。

- 入口點事件,表示程式已到達其主要入口點,如**Main**或`WinMain`。 如果 DE 附加到已運行的程式,則通常不會發送此事件。

  在程式設計上,DE 首先發送作業階段調試管理員 (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)介面,該介面表示引擎創建事件,然後是[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md),它表示程式創建事件。

  這些事件之後通常跟一個或多個[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)線程創建事件和[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)模組載入事件。

  載入代碼並準備執行時,但在執行任何代碼之前,DE 會向 SDM 發送[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)載入完成事件。 最後,如果程式尚未運行,DE 將發送[IDebugEntryPoint2](../../extensibility/debugger/reference/idebugentrypointevent2.md)入口點事件,表示程式已到達其主要入口點並準備好進行調試。

## <a name="see-also"></a>另請參閱
- [執行控制](../../extensibility/debugger/control-of-execution.md)
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
