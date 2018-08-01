---
title: 控制執行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13038e11625bb152f36651d95a1f7fda758bb128
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204189"
---
# <a name="control-of-execution"></a>控制執行
偵錯引擎 (DE) 通常會傳送下列事件的其中一個做為最後一個啟動事件：  
  
-   項目點事件，如果將附加至新推出的程式  
  
-   載入完成事件，如果將附加至已在執行程式  
  
 這兩個這些事件包括停止事件，這表示，DE 等候使用者回應透過 IDE。 如需詳細資訊，請參閱 <<c0> [ 作業模式](../../extensibility/debugger/operational-modes.md)。  
  
## <a name="stopping-event"></a>正在停止事件  
 當 「 停止 」 事件傳送至偵錯工作階段：  
  
1.  「 計畫 」 與 「 包含目前指令指標的執行緒可以取自事件介面。  
  
2.  IDE 判斷目前來源的程式碼檔案，它會顯示成反白顯示在編輯器中的位置。  
  
3.  偵錯工作階段通常會回應此第一個停止事件所呼叫的程式**繼續**方法。  
  
4.  程式接著執行，直到它遇到停止條件，例如叫用中斷點。 在此情況下，d 會將中斷點事件傳送至偵錯工作階段。 中斷點事件已停止 」 事件，並 DE 再等候使用者回應。  
  
5.  如果使用者選擇，逐步執行，或函式，從 IDE 提示時會呼叫該程式的偵錯工作階段`Step`方法。 IDE，然後將步驟 （指令、 陳述式或程式行） 和步驟 （是否要逐步執行，或從函式） 的類型的單位。 步驟完成時，DE 會將步驟完成的事件傳送至偵錯工作階段，也就是停止事件。  
  
     -或-  
  
     如果使用者選擇繼續執行目前指令指標，則 IDE 提示時會呼叫該程式的偵錯工作階段**Execute**方法。 程式會繼續執行，直到遇到下一個的停止條件。  
  
     -或-  
  
     如果偵錯工作階段是要忽略特定的停止事件，偵錯工作階段會呼叫程式的**繼續**方法。 如果程式逐步執行到，進入，或者跳離函式它遇到停止條件時，接下來的步驟。  
  
 以程式設計的方式，當 DE 遇到停止條件，它會傳送這類停止事件中的當做[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或是[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)藉由工作階段偵錯管理員 (SDM)[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 DE 傳遞[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)並[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面來代表程式，並包含目前指令指標的執行緒。 SDM 呼叫[IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)若要取得最上層的堆疊框架並呼叫[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)來取得目前指令與相關聯的文件內容指標。 此文件內容通常是來源的程式碼檔案名稱、 線條與資料行編號。 IDE 會使用這些的原始程式碼，其中包含目前指令指標反白顯示。  
  
 在 SDM 通常會回應此第一個停止事件藉由呼叫[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 然後會在程式執行，直到它遇到停止條件，例如叫用的中斷點，案例 DE 會傳送[IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md)以 SDM。 中斷點事件已停止 」 事件，並 DE 再等候使用者回應。  
  
 如果使用者選擇，逐步執行，或函式，從 IDE 提示時會呼叫 SDM [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)。 然後將傳遞 IDE [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) （指示、 陳述式或線條） 和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)，也就是要逐步執行，或從函式。 步驟完成時，會將傳送 DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) SDM，也就是停止事件的介面。  
  
 如果使用者選擇繼續執行目前指令指標從，IDE 會要求呼叫 SDM [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程式會繼續執行，直到遇到下一個的停止條件。  
  
 偵錯封裝偵錯封裝是否要忽略特定的停止事件，會呼叫 SDM，它會呼叫[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果程式逐步執行到，進入，或者跳離函式它遇到停止條件時，它會繼續步驟。 這表示程式會維護逐步執行的狀態，好讓它知道如何繼續執行。  
  
 在 SDM 對呼叫`Step`， **Execute**，和**繼續**是非同步的這表示在 SDM 預期呼叫快速傳回。 如果 DE SDM 停止將事件傳送之前的相同執行緒上`Step`， **Execute**，或**繼續**傳回，SDM 停止回應。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)