---
title: 執行的控制 |Microsoft Docs
description: 瞭解停止事件，這表示會使用 IDE 來等候使用者的回應。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b00e0529c1d2ac7224881067628618251ba03898
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930508"
---
# <a name="control-of-execution"></a>執行的控制
Debug engine (DE) 通常會將下列其中一個事件傳送為最後一個啟動事件：

- 進入點事件（如果附加至新啟動的程式）

- 載入完成事件（如果附加至已在執行中的程式）

  這兩個事件都是停止事件，這表示會使用 IDE 來等候使用者的回應。 如需詳細資訊，請參閱 [操作模式](../../extensibility/debugger/operational-modes.md)。

## <a name="stopping-event"></a>停止事件
 當停止事件傳送至 debug 會話時：

1. 您可以從事件介面取得包含目前指令指標的程式和執行緒。

2. IDE 會決定目前的原始程式碼檔和位置，並在編輯器中以反白顯示。

3. Debug 會話通常會呼叫程式的 **Continue** 方法，以回應第一個停止事件。

4. 程式接著會執行，直到遇到停止狀況為止，例如叫用中斷點。 在這種情況下，「取消」會將中斷點事件傳送到「debug」會話。 中斷點事件是停止事件，並且會再次等候使用者回應。

5. 如果使用者想要逐步執行、跳過或移出函式，IDE 會提示 debug 會話呼叫程式的 `Step` 方法。 然後，IDE 會將步驟的單位傳遞 (的指令、語句或行) 和步驟的類型 (是否) 逐步執行、跳過或移出函數。 當步驟完成時，會將步驟完成事件傳送至 debug 會話，這是一個停止事件。

    -或-

    如果使用者想要從目前的指令指標中繼續執行，IDE 會提示 debug 會話呼叫程式的 **Execute** 方法。 程式會繼續執行，直到遇到下一個停止狀況為止。

    -或-

    如果 debug 會話要忽略特定的停止事件，debug 會話就會呼叫程式的 **Continue** 方法。 如果程式在遇到停止狀況時進入、跳過或移出函式，則會繼續進行此步驟。

   以程式設計的方式，當 DE 遇到停止狀況時，它會以 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) 或 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) 的方式將事件傳送到會話 debug manager (SDM) 透過 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 介面來進行。 DE 會傳遞代表程式的 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 和 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) 介面，以及包含目前指令指標的執行緒。 SDM 會呼叫 [IDebugThread2：： EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 來取得最上層堆疊框架，並呼叫 [IDebugStackFrame2：： GetDocumentCoNtext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) 來取得與目前指令指標相關聯的檔內容。 此檔內容通常是原始程式碼檔名稱、行號和欄號。 IDE 會使用這些程式碼來反白顯示包含目前指令指標的原始程式碼。

   SDM 通常會藉由呼叫 [IDebugProgram2：： Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)來回應這個第一個停止事件。 程式接著會執行，直到遇到停止狀況為止，例如叫用中斷點，而在此情況下，會將 [IDebugBreakpointEvent2 介面](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 傳送至 SDM。 中斷點事件是停止事件，並且會再次等候使用者回應。

   如果使用者想要逐步執行、跳過或移出函式，IDE 會提示 SDM 呼叫 [IDebugProgram2：： step](../../extensibility/debugger/reference/idebugprogram2-step.md)。 然後，IDE 會將 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 傳遞 (的指令、語句或行) 和 [STEPKIND](../../extensibility/debugger/reference/stepkind.md)，也就是逐步執行、跳過或移出函數。 當步驟完成時，DE 會將 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 介面傳送至 SDM，也就是停止事件。

   如果使用者想要從目前的指令指標中繼續執行，IDE 會要求 SDM 呼叫 [IDebugProgram2：： Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)。 程式會繼續執行，直到遇到下一個停止狀況為止。

   如果 debug 封裝要忽略特定的停止事件，debug 封裝會呼叫 SDM，它會呼叫 [IDebugProgram2：： Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)。 如果程式在遇到停止狀況時進入、跳過或移出函式，它會繼續執行步驟。 這表示程式會維持逐步執行狀態，讓它知道如何繼續進行。

   對 SDM 進行 `Step` 、 **執行** 和 **繼續** 的呼叫是非同步，這表示 sdm 預期呼叫會快速傳回。 如果「取消」會在相同的執行緒上傳送 SDM a 停止事件，然後才會傳回 `Step` 、 **執行** 或 **繼續** ，則 sdm 將會停止回應。

## <a name="see-also"></a>另請參閱
- [調試作業](../../extensibility/debugger/debugging-tasks.md)
