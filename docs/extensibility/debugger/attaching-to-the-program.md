---
title: 附加至程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c9719f6258f3bbb5cc8323693001c7f1a9d47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-to-the-program"></a>附加至程式
您已註冊您的程式與適當的通訊埠之後，您必須將偵錯工具附加至您要偵錯的程式。  
  
## <a name="choosing-how-to-attach"></a>選擇如何將連接  
 有三種方式，工作階段的偵錯管理員 (SDM) 嘗試附加至正在偵錯的程式。  
  
1.  透過偵錯引擎所啟動的程式[LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)方法 （一般解譯的語言，例如） 中，SDM 取得[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)程式附加至相關聯的物件。 如果可以取得 SDM`IDebugProgramNodeAttach2`介面，然後呼叫 SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 `IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_OK`表示不未附加至程式和其他嘗試可能會對附加的程式。  
  
2.  如果可以取得 SDM [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)介面從要附加到 SDM 呼叫程式[附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)方法。 這個方法是典型的遠端連接埠供應商所啟動的程式。  
  
3.  如果無法透過附加程式`IDebugProgramNodeAttach2::OnAttach`或`IDebugProgramEx2::Attach`方法 SDM 載入偵錯引擎 （如果尚未載入） 藉由呼叫`CoCreateInstance`函式，然後呼叫[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。 這個方法是常見的連接埠供應商在本機上啟動的程式。  
  
     也可能會呼叫自訂連接埠供應商`IDebugEngine2::Attach`中的自訂連接埠供應商的實作方法`IDebugProgramEx2::Attach`方法。 通常在此情況下，自訂連接埠供應商會啟動遠端電腦上的偵錯引擎。  
  
 附件在工作階段的偵錯管理員 (SDM) 呼叫時達成[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)方法。  
  
 如果您要偵錯應用程式相同的程序中執行您 DE，則您必須實作下列方法[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)，  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 之後`IDebugEngine2::Attach`呼叫方法時，請遵循這些步驟的實作中`IDebugEngine2::Attach`方法：  
  
1.  傳送[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) SDM 事件物件。 如需詳細資訊，請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。  
  
2.  呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件傳遞給`IDebugEngine2::Attach`方法。  
  
     這會傳回`GUID`用來識別該程式。 `GUID`必須儲存在物件，代表本機程式 DE，而且它必須傳回時`IDebugProgram2::GetProgramId`上呼叫方法`IDebugProgram2`介面。  
  
    > [!NOTE]
    >  如果您實作`IDebugProgramNodeAttach2`介面，該程式`GUID`傳遞至`IDebugProgramNodeAttach2::OnAttach`方法。 這`GUID`用於程式`GUID`傳回`IDebugProgram2::GetProgramId`方法。  
  
3.  傳送[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)通知 SDM 事件物件的本機`IDebugProgram2`以 DE 代表程式建立物件。 如需詳細資訊，請參閱[傳送事件](../../extensibility/debugger/sending-events.md)。  
  
    > [!NOTE]
    >  這不是相同`IDebugProgram2`物件傳遞至`IDebugEngine2::Attach`方法。 先前傳遞`IDebugProgram2`物件的連接埠只會辨識，而且是不同的物件。  
  
## <a name="see-also"></a>另請參閱  
 [啟動為基礎的附件](../../extensibility/debugger/launch-based-attachment.md)   
 [傳送事件](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)