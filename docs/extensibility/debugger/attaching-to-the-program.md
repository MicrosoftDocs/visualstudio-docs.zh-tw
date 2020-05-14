---
title: 附加到程式 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f39b489a57ab93ba5f2d116738c591bd53ff95f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739249"
---
# <a name="attach-to-the-program"></a>附加到程式
在適當的埠註冊程式后,必須將調試器附加到要調試的程式。

## <a name="choose-how-to-attach"></a>選擇如何附加
 會話調試管理員 (SDM) 嘗試附加到正在除錯的程式有三種方式。

1. 對於調試引擎通過[Launch 暫停](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法啟動的程式(例如,典型的解釋語言),SDM 從與所附加到的程式關聯的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)物件獲取[IDebug ProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面。 如果 SDM`IDebugProgramNodeAttach2`可以獲取 介面,則 SDM 然後調用[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 該方法`IDebugProgramNodeAttach2::OnAttach`返回`S_OK`以指示它未附加到程式,並且可以嘗試附加到該程式。

2. 如果 SDM 可以從所附加到的程式獲取[IDebug ProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)介面,則 SDM 將調用[附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。 此方法對於埠供應商遠程啟動的程式是典型的。

3. 如果無法`IDebugProgramNodeAttach2::OnAttach`通過`IDebugProgramEx2::Attach`或方法 附加程式,則 SDM 通過調用`CoCreateInstance`函數載入除錯引擎(如果尚未載入),然後調用[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 此方法對於埠供應商在本地啟動的程式是典型的。

    自定義埠供應商也可以調用`IDebugEngine2::Attach`自定義埠供應商實現該方法`IDebugProgramEx2::Attach`的方法。 在這種情況下,自定義埠供應商在遠端電腦上啟動調試引擎。

   當工作階段除錯管理員 (SDM) 呼叫附加方法時,並[連線](../../extensibility/debugger/reference/idebugengine2-attach.md)。

   如果 DE 與要除錯的應用程式在同一行程中運行,則必須實現[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)的以下方法:

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  呼叫方法`IDebugEngine2::Attach`後,`IDebugEngine2::Attach`在方法的實現中按照以下步驟操作:

1. 將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件發送到 SDM。 有關詳細資訊,請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。

2. 在傳遞給`IDebugEngine2::Attach`該方法的[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)對象上調用[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法。

     這會傳回`GUID`用於識別程式的 。 `GUID`必須存儲在表示 DE 的本地程式的物件中,並且`IDebugProgram2`必須在介面`IDebugProgram2::GetProgramId`上調用 方法時返回它。

    > [!NOTE]
    > 如果實現介面,`IDebugProgramNodeAttach2`程式`GUID`會傳遞給`IDebugProgramNodeAttach2::OnAttach`方法 。 這`GUID`用於`GUID``IDebugProgram2::GetProgramId`方法返回的程式。

3. 發送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件,通知 SDM 本地`IDebugProgram2`物件已創建以向 DE 表示程式。 有關詳細資訊,請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。

    > [!NOTE]
    > 這不是傳遞到`IDebugProgram2``IDebugEngine2::Attach`方法的相同物件。 以前傳遞`IDebugProgram2`的物件僅由埠識別,並且是一個單獨的物件。

## <a name="see-also"></a>另請參閱
- [建基於開機的附件](../../extensibility/debugger/launch-based-attachment.md)
- [傳送事件](../../extensibility/debugger/sending-events.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)
- [附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)
- [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)
