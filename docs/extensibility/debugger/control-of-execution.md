---
title: 控制執行 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a76b14f28bdb74345813931fc334f98090abd93c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="control-of-execution"></a>控制執行
偵錯引擎 (DE) 通常會傳送下列事件之一為最後一個啟動事件：  
  
-   項目點事件，如果將連接至新啟動程式  
  
-   載入完成事件，如果附加到已在執行中的程式  
  
 這兩個這些事件包括停止事件，這表示，DE 等候使用者回應透過 IDE。 如需詳細資訊，請參閱[作業模式](../../extensibility/debugger/operational-modes.md)。  
  
## <a name="stopping-event"></a>正在停止事件  
 當停止事件傳送到偵錯工作階段：  
  
1.  包含目前指令指標的執行緒與程式可從此事件介面。  
  
2.  IDE 會決定目前的原始程式檔和位置，這會顯示在編輯器中反白顯示。  
  
3.  偵錯工作階段通常會回應此第一個停止事件所呼叫的程式**繼續**方法。  
  
4.  程式接著會執行直到它遇到停止條件，例如叫用的中斷點，在其中案例 DE 將中斷點事件傳送至偵錯工作階段為止。 中斷點是停止事件，並 DE 一次等候使用者回應。  
  
5.  如果使用者選擇 [過度]、 逐步執行或離函式，則 IDE 提示時會呼叫程式的偵錯工作階段`Step`方法，傳遞步驟 （指令、 陳述式或程式行） 和步驟的類型的單位，也就是是否要在逐步執行或移到函式。 當完成此步驟之後時，DE 會傳送給偵錯工作階段，也就是停止事件的步驟完成的事件。  
  
     -或-  
  
     如果使用者選擇繼續執行從目前指令指標，則 IDE 提示時會呼叫程式的偵錯工作階段**Execute**方法。 程式會繼續執行直到它遇到下一個的停止條件為止。  
  
     -或-  
  
     如果要忽略特定的停止事件是偵錯工作階段，偵錯工作階段呼叫的程式**繼續**方法。 如果程式已逐步執行到、 不進入或離函式時遇到停止條件，然後它會繼續步驟。  
  
 以程式設計的方式，當 DE 遇到停止條件時，它會傳送這類停止事件中的當做[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)藉由工作階段偵錯管理員 (SDM)[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面。 DE 傳遞[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)和[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)代表程式和執行緒，包含目前指令指標的介面。 SDM 呼叫[IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)以取得最上層的堆疊框架和呼叫[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) ，取得目前指令與相關聯的文件內容指標。 此文件內容通常是原始程式碼的程式碼檔案名稱、 線條與資料行號。 IDE 會使用這些屬性的原始程式碼，包含目前指令指標反白顯示。  
  
 SDM 通常會回應此第一個停止事件藉由呼叫[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 然後會在程式執行，直到它遇到停止條件，例如叫用的中斷點，將案例 DE 傳送[IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md)到 SDM。 中斷點是停止事件，並 DE 一次等候使用者回應。  
  
 如果使用者選擇 [過度]、 逐步執行或離函式，則 IDE 提示時會呼叫 SDM [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)，將其傳遞[STEPUNIT](../../extensibility/debugger/reference/stepunit.md) （指令、 陳述式或程式行） 和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)，也就是是否要逐步執行，或移到函式。 當完成此步驟之後時，會將傳送 DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) SDM，也就是停止事件的介面。  
  
 如果使用者選擇繼續執行目前指令指標從，IDE 會要求呼叫 SDM [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程式會繼續執行直到它遇到下一個的停止條件為止。  
  
 如果要忽略特定的停止事件是偵錯封裝，偵錯封裝呼叫 SDM，它會呼叫[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果程式已逐步執行到、 不進入或離函式時遇到停止條件，然後它會繼續步驟。 這表示程式會維護逐步執行的狀態，使它知道如何繼續進行。  
  
 SDM 對呼叫`Step`， **Execute**，和**繼續**都是非同步的這表示 SDM 預期呼叫快速傳回。 如果 DE SDM 停止將事件傳送之前在相同執行緒上`Step`， **Execute**，或**繼續**傳回 SDM 停止回應。  
  
## <a name="see-also"></a>請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)