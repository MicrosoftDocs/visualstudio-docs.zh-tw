---
title: 傳送所需的事件 |Microsoft Docs
description: 瞭解在建立偵錯工具引擎並將它附加至 Visual Studio 的偵錯工具時，所需的已排序事件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a53f4d7a89b1f5902f576490d827148e9fb816bf
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070371"
---
# <a name="send-the-required-events"></a>傳送所需的事件
使用此程式來傳送所需的事件。

## <a name="process-for-sending-required-events"></a>傳送所需事件的進程
 若要建立偵錯工具引擎 (先) ，並將它附加至程式，則需要下列事件：

1. 將 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) 事件物件傳送至會話 debug MANAGER (SDM) 當取消初始化以在進程中進行一或多個程式的偵錯工具時。

2. 當要進行調試的程式附加至時，會將 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) 事件物件傳送至 SDM。 此事件可能是停止事件，視您的引擎設計而定。

3. 如果程式是在進程啟動時附加到，請將 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) 事件物件傳送至 SDM，以通知 IDE 有新的執行緒。 此事件可能是停止事件，視您的引擎設計而定。

4. 當正在進行偵錯工具的程式完成載入或附加至程式完成時，將 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 事件物件傳送至 SDM。 此事件必須是停止事件。

5. 如果要啟動的應用程式已啟動，則在執行時間架構中的第一個程式碼指令即將執行時，將 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 事件物件傳送至 SDM。 此事件一律為停止事件。 在逐步執行調試的會話時，IDE 會在此事件上停止。

> [!NOTE]
> 許多語言都使用全域初始化運算式或外部、先行編譯函式 (自 CRT 程式庫，或在其程式碼開頭 _Main) 。 如果您要進行偵錯工具的語言在初始進入點之前包含這其中一種類型的元素，則會執行此程式碼，並在到達使用者進入點（例如 **main** 或）時傳送進入點事件 `WinMain` 。

## <a name="see-also"></a>另請參閱
- [啟用要進行調試的程式](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
