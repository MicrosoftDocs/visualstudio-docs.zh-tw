---
title: 啟動後附加 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739278"
---
# <a name="attach-after-a-launch"></a>啟動後附加
程序啟動後,調試會話已準備好將調試引擎 (DE) 附加到上述程式。

## <a name="design-decisions"></a>設計決策
 由於在共用位址空間內通信更容易,因此必須在兩種設計方法之間進行選擇:在調試會話和 DE 之間設置通信。 或者,設置 DE 和程式之間的通信。 在以下兩者之間選擇:

- 如果設置調試會話和 DE 之間的通訊更有意義,則調試會話將共同創建 DE,並要求 DE 附加到程式。 此設計將除錯工作階段和 DE 放在一個位址空間中,並將執行時環境和程式放在另一個位址空間中。

- 如果設置 DE 和程式之間的通信更有意義,則執行時環境將共同創建 DE。 此設計將 SDM 保留在一個位址空間和 DE、執行時環境和程式一起放在另一個位址空間中。 此設計是典型的 DE,該 DE 使用解釋器實現以運行文本語言。

    > [!NOTE]
    > DE 如何附加到程序取決於實現。 DE 和程式之間的通信也依賴於實現。

## <a name="implementation"></a>實作
 在程式設計上,當會話調試管理器 (SDM) 首次收到表示要啟動的程式的[IDebug Program2](../../extensibility/debugger/reference/idebugprogram2.md)物件時,它將調用[Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法,將其傳遞為[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)物件,該物件後來用於將調試事件傳回 SDM。 然後`IDebugProgram2::Attach`,該方法調用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 有關 SDM`IDebugProgram2`如何接收 介面的詳細資訊,請參閱[通知埠](../../extensibility/debugger/notifying-the-port.md)。

 如果 DE 需要在與正在除錯的應用程式相同的位址空間中執行:因為 DE 通常是執行文稿的解釋器`IDebugProgramNodeAttach2::OnAttach`的一部分,`S_FALSE`因此該方法將傳回 。 `S_FALSE`返回表示已完成附加過程。

 但是,如果 DE 在 SDM`IDebugProgramNodeAttach2::OnAttach`的位址空間 中`S_OK`運行:該方法返回 ,或者[IDebugProgramNode Attach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面根本不在與要調試的程式關聯的[IDebug ProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)對象上實現。 在這種情況下,最終調用[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)方法以完成附加操作。

 在後一種情況下,必須在傳遞給`IDebugProgram2``IDebugEngine2::Attach`該方法的物件上調`GUID`用[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法,將存儲在本地程式物件中,並在`IDebugProgram2::GetProgramId`隨後調用 此`GUID`物件的方法時返回 此方法。 `GUID`用於在各種調試元件中唯一地標識程式。

 `IDebugProgramNodeAttach2::OnAttach`在返回的方法中`S_FALSE`,用於程式`GUID`的 將傳遞給該`IDebugProgramNodeAttach2::OnAttach`方法, 它是在`GUID`本地程式物件 上設置的方法。

 DE 現在附加到該程式,並準備發送任何啟動事件。

## <a name="see-also"></a>另請參閱
- [直接附加到程式](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [通知連接埠](../../extensibility/debugger/notifying-the-port.md)
- [除錯工作](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)
