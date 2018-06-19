---
title: 在啟動後附加 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69f9f9cde76c5fa66294fd2cdbdc5252169e0183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31104702"
---
# <a name="attaching-after-a-launch"></a>在啟動後附加
已啟動程式之後，偵錯工作階段已附加偵錯引擎 (DE) 至前述的程式。  
  
## <a name="design-decisions"></a>設計決策  
 由於通訊是更容易在共用的位址空間內，您必須決定是否合理的更多協助偵錯工作階段，以 DE 或 DE 與程式之間的通訊。 選擇下列兩者：  
  
-   如果它更具意義以便偵錯工作階段與 DE 之間的通訊，偵錯工作階段就會同時建立 DE 檔案，並要求附加至程式 DE 中。 這會保留偵錯工作階段，以 DE 一起在一個位址空間的執行階段環境和程式一起放在另一個。  
  
-   如果它更具意義為了促進 DE 與程式之間的通訊，然後執行階段環境共同建立 DE。 這會保留一個位址空間中的 SDM DE、 執行階段環境和程式一起放在另一個。 這是一般的實作與執行已編寫指令碼的語言解譯器將 DE。  
  
    > [!NOTE]
    >  DE 將附加至程式的方式是視實作而定。 DE 與程式之間的通訊也是視實作而定。  
  
## <a name="implementation"></a>實作  
 以程式設計的方式，當工作階段的偵錯管理員 (SDM) 第一次收到[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件，代表要啟動程式，它會呼叫[附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法，將它傳遞給[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)物件，它是稍後用來傳遞回 SDM 偵錯事件。 `IDebugProgram2::Attach`方法接著呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如需有關如何接收 SDM`IDebugProgram2`介面，請參閱[通知連接埠](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果您 DE 需要在相同的位址空間，做為程式偵錯時，通常是因為 DE 是執行指令碼中，解譯器的一部分執行`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_FALSE`，指出它完成 attach 程序。  
  
 如果相反地，DE 會在位址空間的 SDM`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_OK`或[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面不完全在實作[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)與正在偵錯的程式相關聯的物件。 在此情況下，[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)最後會呼叫方法來完成附加作業。  
  
 在後者的情況下，您必須呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法`IDebugProgram2`物件傳遞給`IDebugEngine2::Attach`方法中，存放區`GUID`本機程式物件，並傳回這個`GUID`時`IDebugProgram2::GetProgramId`方法之後呼叫此物件上。 `GUID`用來唯一識別跨各種偵錯元件的程式。  
  
 請注意，如果是`IDebugProgramNodeAttach2::OnAttach`方法傳回`S_FALSE`、`GUID`要用於程式傳遞至該方法，而且很`IDebugProgramNodeAttach2::OnAttach`方法，以設定`GUID`本機程式物件上。  
  
 DE 現在已附加到程式並準備好要傳送的任何啟動事件。  
  
## <a name="see-also"></a>另請參閱  
 [直接附加程式](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [通知連接埠](../../extensibility/debugger/notifying-the-port.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)