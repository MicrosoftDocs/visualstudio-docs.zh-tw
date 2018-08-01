---
title: 在啟動後附加 |Microsoft Docs
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
ms.openlocfilehash: b767ef1aeed691255a62a9cb5c1e264034acf24e
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39152905"
---
# <a name="attach-after-a-launch"></a>在啟動後附加
程式啟動之後，偵錯工作階段已附加偵錯引擎 (DE) 至前述的程式。  
  
## <a name="design-decisions"></a>設計決策  
 因為通訊是更容易在共用的位址空間內，您必須選擇兩種設計方法： 設定偵錯工作階段和裝置之間的通訊。 或者，設定 DE 與程式之間的通訊。 選擇下列兩者之一：  
  
-   如果較為合理設為偵錯工作階段和裝置之間的通訊，偵錯工作階段 DE 會同時建立，並要求將附加至程式 DE。 這項設計會保留偵錯工作階段，以 DE 一起在一個位址空間的執行階段環境與程式一起放在另一個。  
  
-   如果較為合理設為德國與程式之間的通訊，執行階段環境會同時建立 DE。 這項設計會留下一個位址空間和 DE、 執行階段環境，以及計劃中的 SDM 一起放在另一個。 這項設計是典型的規定與解譯器，以執行指令碼的語言實作的。  
  
    > [!NOTE]
    >  DE 將附加至程式的方式會視實作而定。 DE 與程式之間的通訊也會視實作而定。  
  
## <a name="implementation"></a>實作  
 以程式設計的方式，當工作階段的偵錯管理員 (SDM) 先收到[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件，表示要啟動的程式，它會呼叫[附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法，並傳遞它[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)物件，也就是更新用來傳遞回到 SDM 的偵錯事件。 `IDebugProgram2::Attach`然後方法會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如需有關如何接收 SDM`IDebugProgram2`介面，請參閱 <<c2> [ 通知連接埠](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果您的裝置必須在相同的位址空間，做為程式中執行您在偵錯： 因為 DE 通常是正在執行的指令碼中，解譯器的一部分`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_FALSE`。 `S_FALSE`傳回指出它已完成附加程序。  
  
 如果，不過，裝置會在執行 SDM 的位址空間：`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_OK`，或有[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)不完全在實作介面[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)在偵錯的程式相關聯的物件。 在此情況下，[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)最後會呼叫方法來完成附加作業。  
  
 在後者的情況下，您必須呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法`IDebugProgram2`物件傳遞給`IDebugEngine2::Attach`方法中，存放區`GUID`中的本機程式物件，並傳回這個`GUID`時`IDebugProgram2::GetProgramId`方法之後呼叫此物件上。 `GUID`用來唯一識別跨各種不同的偵錯元件的程式。  
  
 情況`IDebugProgramNodeAttach2::OnAttach`方法傳回`S_FALSE`，則`GUID`要用於程式傳遞至該方法，而且`IDebugProgramNodeAttach2::OnAttach`方法，以設定`GUID`上的本機程式物件。  
  
 DE 現在已附加至程式，並準備好要傳送任何啟動事件。  
  
## <a name="see-also"></a>另請參閱  
 [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md)   
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