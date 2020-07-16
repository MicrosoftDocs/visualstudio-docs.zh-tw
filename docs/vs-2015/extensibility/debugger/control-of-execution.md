---
title: 執行控制 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c885c0c983e6fafd69d55b3d68f8ed6e8ff2628c
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387261"
---
# <a name="control-of-execution"></a>控制執行
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debug engine （DE）通常會將下列其中一個事件當做最後一個啟動事件來傳送：  
  
- 如果附加至新啟動的程式，則為進入點事件  
  
- 載入完成事件（如果附加至已在執行的程式）  
  
  這兩個事件都是停止事件，這表示 DE 會透過 IDE 來等待使用者回應。 如需詳細資訊，請參閱[操作模式](../../extensibility/debugger/operational-modes.md)。  
  
## <a name="stopping-event"></a>停止事件  
 當停止事件傳送至 debug 會話時：  
  
1. 包含目前指令指標的程式和執行緒可以從事件介面取得。  
  
2. IDE 會決定目前的原始程式碼檔案和位置，其在編輯器中會反白顯示。  
  
3. Debug 會話通常會藉由呼叫程式的**Continue**方法來回應第一個停止事件。  
  
4. 程式接著會執行直到遇到停止條件，例如叫用中斷點，在此情況下，DE 會將中斷點事件傳送至 debug 會話。 中斷點事件是一個停止事件，然後再次取消執行以等待使用者回應。  
  
5. 如果使用者想要逐步執行、跳過或跳出函式，IDE 會提示 debug 會話呼叫程式的 `Step` 方法，並將步驟的單位（指令、語句或行）和步驟類型（也就是逐步執行、跳過或移出函式）傳遞給它。 當步驟完成時，[取消] 會將步驟完成事件傳送至 debug 會話，也就是「停止」事件。  
  
    -或-  
  
    如果使用者想要從目前的指令指標繼續執行，IDE 會提示 [debug] 會話呼叫程式的**Execute**方法。 程式會繼續執行，直到它遇到下一個停止條件。  
  
    -或-  
  
    如果 debug 會話是要忽略特定的停止事件，則 debug 會話會呼叫程式的**Continue**方法。 如果程式在遇到停止條件時，在函式中逐步執行、跳過或跳出，則會繼續進行此步驟。  
  
   以程式設計方式來說，當 DE 遇到停止狀況時，它會透過[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)介面，以[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)或[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)的方式將這類停止事件傳送至會話 debug manager （SDM）。 DE 會傳遞代表程式的[IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)和[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)介面，以及包含目前指令指標的執行緒。 SDM 會呼叫[IDebugThread2：： EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)以取得最上層堆疊框架，並呼叫[IDebugStackFrame2：： GetDocumentCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)來取得與目前指令指標相關聯的檔內容。 此檔內容通常是原始程式碼檔名稱、行號和欄號。 IDE 會使用這些程式碼來反白顯示包含目前指令指標的原始程式碼。  
  
   SDM 通常會藉由呼叫[IDebugProgram2：： Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)來回應第一個停止事件。 程式接著會執行，直到遇到停止條件（例如叫用中斷點），在此情況下，DE 會將[IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md)傳送至 SDM。 中斷點事件是一個停止事件，然後再次取消執行以等待使用者回應。  
  
   如果使用者想要逐步執行、跳過或跳出函式，IDE 會提示 SDM 呼叫[IDebugProgram2：： step](../../extensibility/debugger/reference/idebugprogram2-step.md)，將[STEPUNIT](../../extensibility/debugger/reference/stepunit.md) （指令、語句或行）和[STEPKIND](../../extensibility/debugger/reference/stepkind.md)（也就是逐步執行、跳過或移出函式）傳遞給它。 當步驟完成時，DE 會將[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)介面傳送至 SDM，這是停止事件。  
  
   如果使用者想要從目前的指令指標繼續執行，IDE 會要求 SDM 呼叫[IDebugProgram2：： Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程式會繼續執行，直到它遇到下一個停止條件。  
  
   如果 debug 封裝是要忽略特定的停止事件，則 debug 封裝會呼叫 SDM，而後者會呼叫[IDebugProgram2：： Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果程式在遇到停止條件時，在函式中逐步執行、跳過或跳出，則會繼續進行此步驟。 這表示程式會維持逐步執行狀態，讓它知道如何繼續進行。  
  
   SDM 進行的呼叫 `Step` 、**執行**和**繼續**都是非同步，這表示 sdm 預期該呼叫會快速傳回。 如果在執行或繼續傳回之前，DE 會在同一個執行緒上傳送一則停止事件給 SDM， `Step` 則 sdm 會停止回應。 **Execute** **Continue**  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)
