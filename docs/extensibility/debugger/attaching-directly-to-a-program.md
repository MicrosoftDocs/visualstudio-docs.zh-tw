---
title: 附加至程式直接 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6885cb0dea801ab95e2e88e3f8168c139fea0e0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100373"
---
# <a name="attaching-directly-to-a-program"></a>直接附加程式
使用者想要偵錯程式已在通常執行的處理序中遵循這個程序：  
  
1.  在 IDE 中，選擇 **偵錯處理序**命令**工具**功能表。  
  
     **處理程序** 對話方塊隨即出現。  
  
2.  選擇處理程序，然後按一下**附加** 按鈕。  
  
     **附加至處理序** 對話方塊隨即顯示，列出電腦上安裝所有的偵錯引擎 (DEs)。  
  
3.  指定要用於偵錯選取的處理序，然後按一下 DEs**確定**。  
  
 偵錯封裝會啟動偵錯工作階段，並將 DEs 清單傳遞給它。 接著再將此清單中，回呼函式，以選取的處理序，以及傳遞偵錯工作階段，並詢問該列舉其執行中的程式的程序。  
  
 以程式設計的方式，以回應使用者要求，偵錯封裝會產生工作階段的偵錯管理員 (SDM)，並且將選取的 DEs 清單傳遞給它。 清單中，以及偵錯封裝傳遞 SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 偵錯封裝將 DEs 清單傳遞至所選處理序藉由呼叫[IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)。 然後呼叫 SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)列舉處理序中執行的程式的連接埠上。  
  
 從這裡開始，每個偵錯引擎會附加至程式完全中所述[附加之後啟動](../../extensibility/debugger/attaching-after-a-launch.md)，有兩種例外。  
  
 為了提高效率，DEs，實作 SDM 與共用的位址空間已分組，因此每個 DE 有的程式會將它附加至一組。 在此情況下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)呼叫[IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ，並將它附加至程式的陣列。  
  
 第二個例外情況是，附加到已在執行中的程式 DE 所傳送的啟動事件不通常包含項目點事件。  
  
## <a name="see-also"></a>另請參閱  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)