---
title: 在啟動後附加 |Microsoft Docs
description: 當程式啟動時，就可以將 debug engine 附加至程式。 選擇與 debug engine 進行通訊的設計方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 22ce6497b820e1dcd37315f9d74cb97de4cc34e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837732"
---
# <a name="attach-after-a-launch"></a>在啟動後附加
程式啟動之後，就可以將偵錯工具附加 (DE) 的程式。

## <a name="design-decisions"></a>設計決策
 因為共用位址空間內的通訊比較容易，所以您必須在兩個設計方法之間做選擇：設定 debug 會話與 DE 之間的通訊。 或者，設定 DE 和程式之間的通訊。 選擇下列各項：

- 如果設定 debug 會話與 DE 之間的通訊更加合理，則 debug 會話會共同建立 DE，並要求 DE 附加至程式。 這項設計會將 debug 會話和一起放在同一個位址空間中，並將執行時間環境和程式一起放在另一個位址空間中。

- 如果設定 DE 和程式之間的通訊更加合理，則執行時間環境會共同建立 DE。 這項設計會將 SDM 保留在一個位址空間中，並將 DE、執行時間環境和程式一起放在另一個位址空間中。 這項設計通常是使用解譯器來執行指令碼語言的 DE。

    > [!NOTE]
    > 「取消附加至程式」與「執行相依」的方式。 DE 和程式之間的通訊也會與執行相依。

## <a name="implementation"></a>實作
 以程式設計的方式，當會話 debug manager (SDM) 先接收代表要啟動之程式的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 物件時，它會呼叫 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 方法，並 [將它](../../extensibility/debugger/reference/idebugeventcallback2.md) 傳遞給它，稍後用來將偵錯工具事件傳遞回 SDM。 `IDebugProgram2::Attach`然後，方法會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如需有關 SDM 如何接收介面的詳細資訊 `IDebugProgram2` ，請參閱 [通知埠](../../extensibility/debugger/notifying-the-port.md)。

 如果您的 DE 必須在與您要進行偵錯工具的相同位址空間中執行：因為 DE 通常是執行腳本的解譯器的一部分，所以此 `IDebugProgramNodeAttach2::OnAttach` 方法會傳回 `S_FALSE` 。 傳回 `S_FALSE` 表示它已完成附加進程。

 但是，如果取消刪除會在 SDM 的位址空間中執行：方法會傳回 `IDebugProgramNodeAttach2::OnAttach` `S_OK` ，或 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 介面完全不會在與您要進行偵錯工具關聯的 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 物件上執行。 在此情況下，最後會呼叫 [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法來完成附加作業。

 在後者的情況下，您必須在傳遞給方法的物件上呼叫 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 方法 `IDebugProgram2` `IDebugEngine2::Attach` ，將儲存 `GUID` 在本機程式物件中，並在 `GUID` `IDebugProgram2::GetProgramId` 後續針對此物件呼叫方法時傳回此方法。 `GUID`用來在各種不同的 debug 元件之間，唯一地識別程式。

 在傳回方法的情況下 `IDebugProgramNodeAttach2::OnAttach` `S_FALSE` ，要用於 `GUID` 程式的會傳遞至該方法，而這是在 `IDebugProgramNodeAttach2::OnAttach` `GUID` 本機程式物件上設定的方法。

 現在已將 DE 附加至程式，並準備好傳送任何啟動事件。

## <a name="see-also"></a>另請參閱
- [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [通知埠](../../extensibility/debugger/notifying-the-port.md)
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)
