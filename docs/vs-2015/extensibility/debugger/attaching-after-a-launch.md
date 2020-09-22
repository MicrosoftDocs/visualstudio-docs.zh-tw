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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839243"
---
# <a name="attaching-after-a-launch"></a>在啟動後附加
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

啟動程式之後，就可以將偵錯工具附加至已 (DE) 的程式。  
  
## <a name="design-decisions"></a>設計決策  
 由於共用位址空間內的通訊比較容易，因此您必須決定是否要讓偵錯工具和 de 之間的通訊更有意義，或在 DE 和程式之間進行通訊。 選擇下列各項：  
  
- 如果讓 debug 會話與 DE 之間的通訊更加合理，則偵錯工具會話會共同建立 DE，並要求 DE 附加至程式。 這會讓偵錯工具在一個位址空間中保持在一起，並將執行時間環境和程式一起放在另一個位址空間中。  
  
- 如果讓 DE 和程式之間的通訊更加合理，則執行時間環境會共同建立 DE。 這會將 SDM 保留在一個位址空間中，並將 DE、執行時間環境和程式一起放在另一個位址空間中。 這通常是使用解譯器來執行指令碼語言的 DE。  
  
    > [!NOTE]
    > 「取消附加至程式」與「執行相依」的方式。 DE 和程式之間的通訊也會與執行相依。  
  
## <a name="implementation"></a>實作  
 以程式設計的方式，當會話 debug manager (SDM) 先接收代表要啟動之程式的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 物件時，它會呼叫 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) 方法，並 [將它](../../extensibility/debugger/reference/idebugeventcallback2.md) 傳遞給它，稍後用來將偵錯工具事件傳遞回 SDM。 `IDebugProgram2::Attach`然後，方法會呼叫[OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)方法。 如需有關 SDM 如何接收介面的詳細資訊 `IDebugProgram2` ，請參閱 [通知埠](../../extensibility/debugger/notifying-the-port.md)。  
  
 如果您的 DE 需要在與所要進行的程式相同的位址空間中執行，通常是因為 DE 是執行腳本之解譯器的一部分， `IDebugProgramNodeAttach2::OnAttach` 方法 `S_FALSE` 會傳回，表示它已完成附加進程。  
  
 另一方面，如果取消刪除是在 SDM 的位址空間中執行，則方法會傳回， `IDebugProgramNodeAttach2::OnAttach` `S_OK` 或 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 介面完全不會在與所要進行的程式相關聯的 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 物件上執行。 在此情況下，最後會呼叫 [attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 方法來完成附加作業。  
  
 在後者的情況下，您必須在傳遞給方法的物件上呼叫 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 方法 `IDebugProgram2` `IDebugEngine2::Attach` ，將儲存 `GUID` 在本機程式物件中，並在 `GUID` `IDebugProgram2::GetProgramId` 後續針對此物件呼叫方法時傳回此方法。 `GUID`用來在各種不同的 debug 元件之間，唯一地識別程式。  
  
 請注意，在 `IDebugProgramNodeAttach2::OnAttach` 傳回方法的情況下 `S_FALSE` ，要用於程式的 `GUID` 會傳遞至該方法，而且它是在 `IDebugProgramNodeAttach2::OnAttach` `GUID` 本機程式物件上設定的方法。  
  
 現在已將 DE 附加至程式，並準備好傳送任何啟動事件。  
  
## <a name="see-also"></a>另請參閱  
 [直接附加至程式](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [通知埠](../../extensibility/debugger/notifying-the-port.md)   
 [調試作業](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [附加](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [附加](../../extensibility/debugger/reference/idebugengine2-attach.md)
