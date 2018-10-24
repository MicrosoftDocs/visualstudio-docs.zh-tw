---
title: 直接附加至程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de07b2fc8846bd24bb3e4483c78eb339d9d49e4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817543"
---
# <a name="attaching-directly-to-a-program"></a>直接附加至程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

想要偵錯程式已在通常執行的處理序中的使用者，請遵循此程序：  
  
1. 在 IDE 中，選擇**偵錯的處理程序**命令**工具**功能表。  
  
    [處理序] 對話方塊隨即出現。  
  
2. 選擇處理程序，然後按一下**附加** 按鈕。  
  
    **附加至處理序** 對話方塊隨即顯示，列出電腦上安裝所有偵錯引擎 (DEs)。  
  
3. 指定用以偵錯選取的處理序，然後按一下 DEs**確定**。  
  
   偵錯封裝會啟動偵錯工作階段，並傳遞給它的 DEs 的清單。 接著再將傳遞這份清單，以及選取的處理序中，回呼函式，偵錯工作階段，並詢問該列舉其執行程式的程序。  
  
   以程式設計的方式，以回應使用者要求，偵錯封裝會具現化工作階段的偵錯管理員 (SDM)，並將所選的 DEs 清單傳遞給它。 清單中，以及偵錯封裝傳遞 SDM [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 偵錯封裝傳遞給選取的處理序的 DEs 清單，藉由呼叫[IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)。 然後呼叫 SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)列舉處理序中執行的程式在連接埠上。  
  
   從這裡開始，每個偵錯引擎會附加至程式完全中所述[附加之後啟動](../../extensibility/debugger/attaching-after-a-launch.md)，有兩個例外狀況。  
  
   為了提高效率，實作以 SDM 與共用的位址空間的 DEs 已分組，因此每個裝置都有的程式會將它連接至一組。 在此情況下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)呼叫[IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)並將它傳遞的程式附加到陣列。  
  
   第二個例外情況是，所附加到已在執行中的程式 DE 傳送啟動事件不通常包含項目點事件。  
  
## <a name="see-also"></a>另請參閱  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)

