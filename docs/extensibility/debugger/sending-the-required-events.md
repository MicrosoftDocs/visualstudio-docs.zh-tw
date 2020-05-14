---
title: 傳送所需事件 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713001"
---
# <a name="send-the-required-events"></a>傳送所需事件
使用此過程發送所需事件。

## <a name="process-for-sending-required-events"></a>傳送所需事件的過程
 依此順序,建立除錯引擎 (DE) 並將其附加到程式時,需要以下事件:

1. 當 DE 初始化以除錯行程中的一個或多個程式時,將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件發送到工作階段調試管理員 (SDM)。

2. 將要除錯的程式附加到時,將[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件發送到SDM。 此事件可能是停止事件,具體取決於您的發動機設計。

3. 如果程式在啟動進程時附加到,則向 SDM 發送[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)事件物件以通知新線程的 IDE。 此事件可能是停止事件,具體取決於您的發動機設計。

4. 當正在除錯的程式完成載入或附加到程式時,將[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)事件物件發送到 SDM。 此事件必須是停止事件。

5. 如果啟動要調試的應用程式,則在運行時體系結構中的第一個代碼指令即將執行時,向 SDM 發送[IDebugEntryPoint2](../../extensibility/debugger/reference/idebugentrypointevent2.md)事件物件。 此事件始終是停止事件。 踏入調試會話時,IDE 將在此事件中停止。

> [!NOTE]
> 許多語言在其代碼的開頭使用全域初始化程式或外部預編譯函數(來自 CRT 庫或_Main)。 如果要除錯的程式的語言在初始入口點之前包含這些類型的元素之一,則運行此代碼,並在達到使用者入口點(如**主**或`WinMain`)時發送入口點事件。

## <a name="see-also"></a>另請參閱
- [開啟對程式進行除錯](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
