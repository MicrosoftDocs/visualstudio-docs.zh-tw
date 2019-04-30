---
title: 在啟動後附加 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437440"
---
# <a name="attaching-after-a-launch"></a>在啟動後附加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

已啟動程式後，偵錯工作階段已附加偵錯引擎 (DE) 至前述的程式。  
  
## <a name="design-decisions"></a>設計決策  
 因為通訊是更容易在共用的位址空間內，您必須決定是否較為合理以便或之間偵錯工作階段和德國，DE 與程式之間的通訊。 選擇下列兩者之一：  
  
- 如果較為合理以便偵錯工作階段和裝置之間的通訊，偵錯工作階段就會同時建立 DE 檔案，並要求附加至程式 DE 中。 這可讓偵錯工作階段，以 DE 一起在一個位址空間的執行階段環境與程式一起放在另一個。  
  
- 如果較為合理促進 DE 與程式之間的通訊，然後執行階段環境共同建立 DE。 這會保留在一個位址空間中，SDM DE、 執行階段環境和程式一起放在另一個。 這是典型的規定與解譯器，以執行指令碼的語言實作。  
  
    > [!NOTE]
    > DE 將附加至程式的方式會視實作而定。 DE 與程式之間的通訊也會視實作而定。  
  
## <a name="implementation"></a>實作  
 以程式設計的方式，當工作階段的偵錯管理員 (SDM) 先收到[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)物件，表示要啟動的程式，它會呼叫[附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)方法，並傳遞它[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)物件，也就是更新用來傳遞回到 SDM 的偵錯事件。 `IDebugProgram2::Attach`然後方法會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如需有關如何接收 SDM`IDebugProgram2`介面，請參閱 <<c2> [ 通知連接埠](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果需要在相同的位址空間，和正在偵錯，通常是因為 DE 屬於解譯器執行指令碼，該程式中執行您 DE`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_FALSE`，指出它完成附加程序。  
  
 如果 DE SDM，位址空間中執行的相反地，`IDebugProgramNodeAttach2::OnAttach`方法會傳回`S_OK`或[IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)介面的實作不完全在[IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)正在偵錯程式相關聯的物件。 在此情況下，[附加](../../extensibility/debugger/reference/idebugengine2-attach.md)最後會呼叫方法來完成附加作業。  
  
 在後者的情況下，您必須呼叫[GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)方法`IDebugProgram2`物件傳遞給`IDebugEngine2::Attach`方法中，存放區`GUID`中的本機程式物件，並傳回這個`GUID`時`IDebugProgram2::GetProgramId`方法之後呼叫此物件上。 `GUID`用來唯一識別跨各種不同的偵錯元件的程式。  
  
 請注意，若是`IDebugProgramNodeAttach2::OnAttach`方法傳回`S_FALSE`，則`GUID`要用於程式傳遞至該方法，而且`IDebugProgramNodeAttach2::OnAttach`方法，以設定`GUID`本機程式物件上。  
  
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
