---
title: 附加至程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 00b9780d0d302b9e067feed057d1a8d49c5f9fc0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903221"
---
# <a name="attach-to-the-program"></a>附加至程式
在您使用適當的埠註冊程式之後，您必須將偵錯工具附加至您要進行 debug 的程式。

## <a name="choose-how-to-attach"></a>選擇附加方式
 有三種方式可將會話偵錯工具（SDM）嘗試附加至正在進行調試的程式。

1. 針對由 debug engine 透過[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法啟動的程式（例如，典型的轉譯語言），SDM 會從與所附加之程式相關聯的[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)物件取得[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面。 如果 SDM 可以取得 `IDebugProgramNodeAttach2` 介面，則 sdm 會接著呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 方法會傳回， `IDebugProgramNodeAttach2::OnAttach` `S_OK` 表示它未附加至程式，而且可以將其他嘗試附加至程式。

2. 如果 SDM 可以從所附加的程式中取得[IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)介面，則 sdm 會呼叫[Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。 這種方法通常適用于由埠供應商遠端啟動的程式。

3. 如果程式無法透過 `IDebugProgramNodeAttach2::OnAttach` 或 `IDebugProgramEx2::Attach` 方法附加，SDM 會藉由呼叫函式來載入 debug engine （如果尚未載入）， `CoCreateInstance` 然後呼叫[Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 這種方法通常適用于埠供應商在本機啟動的程式。

    自訂通訊埠供應商也可以 `IDebugEngine2::Attach` 在方法的自訂埠供應商的執行中呼叫方法 `IDebugProgramEx2::Attach` 。 一般來說，在此情況下，自訂通訊埠供應商會在遠端電腦上啟動調試引擎。

   當會話 debug manager （SDM）呼叫 Attach 方法時，就會達成[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)檔案。

   如果您在與要進行調試的應用程式相同的進程中執行 DE，則必須執行下列[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)方法：

- [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)

- [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)

- [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)

  `IDebugEngine2::Attach`呼叫方法之後，請在方法的執行中遵循下列步驟 `IDebugEngine2::Attach` ：

1. 將[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)事件物件傳送至 SDM。 如需詳細資訊，請參閱傳送[事件](../../extensibility/debugger/sending-events.md)。

2. 在傳遞至方法的[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件上呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法 `IDebugEngine2::Attach` 。

     這會傳回 `GUID` 用來識別程式的。 `GUID`必須儲存在代表解除的本機程式之物件中，而且必須在 `IDebugProgram2::GetProgramId` 介面上呼叫方法時傳回。 `IDebugProgram2`

    > [!NOTE]
    > 如果您執行 `IDebugProgramNodeAttach2` 介面，則會將程式 `GUID` 的傳遞給 `IDebugProgramNodeAttach2::OnAttach` 方法。 這 `GUID` 會用於方法所傳回的程式 `GUID` `IDebugProgram2::GetProgramId` 。

3. 傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)事件物件，以通知 SDM `IDebugProgram2` 已建立本機物件來代表要解除的程式。 如需詳細資訊，請參閱傳送[事件](../../extensibility/debugger/sending-events.md)。

    > [!NOTE]
    > 這不是 `IDebugProgram2` 傳遞至方法的相同物件 `IDebugEngine2::Attach` 。 先前傳遞的 `IDebugProgram2` 物件只會由埠辨識，而且是個別的物件。

## <a name="see-also"></a>另請參閱
- [以啟動為基礎的附件](../../extensibility/debugger/launch-based-attachment.md)
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
