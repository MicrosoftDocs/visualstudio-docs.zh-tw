---
title: 直接附加至程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147993"
---
# <a name="attaching-directly-to-a-program"></a>直接附加至程式
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

如果使用者想要在已經在執行的進程中進行程式偵錯工具，通常會遵循此進程：  
  
1. 在 IDE 中，從 [**工具**] 功能表選擇 [ **Debug 進程**] 命令。  
  
    [處理序]**** 對話方塊隨即出現。  
  
2. 選擇處理常式，然後按一下 [ **附加** ] 按鈕。  
  
    [ **附加至進程** ] 對話方塊隨即出現，列出電腦上已安裝 (DEs) 的所有偵錯工具引擎。  
  
3. 指定要用來偵測所選進程的 DEs，然後按一下 **[確定]**。  
  
   Debug 封裝會啟動一個 debug 會話，並將 DEs 清單傳遞給它。 接著，debug 會話會將這份清單連同回呼函式傳遞至選取的進程，然後要求進程列舉其執行的程式。  
  
   以程式設計的方式，為了回應使用者要求，debug 封裝會具現化會話 debug manager (SDM) ，並將選取的 DEs 清單傳遞給它。 除了清單，debug 封裝也會將 SDM 傳遞給 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 介面。 Debug 封裝會藉由呼叫 [IDebugProcess2：： Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)，將 DEs 清單傳遞至選取的進程。 然後 SDM 會在埠上呼叫 [IDebugProcess2：： EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) ，以列舉在進程中執行的程式。  
  
   從此時開始，每個偵錯工具都會附加至程式，完全如同在 [啟動後附加](../../extensibility/debugger/attaching-after-a-launch.md)的詳細資訊，但有兩個例外狀況。  
  
   為了提高效率，會將用來與 SDM 共用位址空間的 DEs 進行分組，讓每一次刪除都有一組要附加的程式。 在此情況下， [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 會呼叫 [IDebugEngine2：： attach](../../extensibility/debugger/reference/idebugengine2-attach.md) ，然後將要附加的程式陣列傳遞給它。  
  
   第二個例外狀況是，當附加至已在執行中的程式所傳送的啟動事件通常不會包含進入點事件。  
  
## <a name="see-also"></a>另請參閱  
 [在啟動後傳送啟動事件](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)
